# codedump
An unorganized reference dump for me.

- [AWS: How to Mount S3 Bucket Using IAM Role on EC2 Linux instance](https://medium.com/tensult/aws-how-to-mount-s3-bucket-using-iam-role-on-ec2-linux-instance-ad2afd4513ef)
- [How To Serve Django Applications with uWSGI and Nginx on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-uwsgi-and-nginx-on-ubuntu-16-04#install-and-configure-virtualenv-and-virtualenvwrapper)
- Testing SMTP servers with `swaks` example
  ```
  swaks --to areebbeigh@gmail.com \
    --from noreply@example.com \
    --server email-smtp.ap-east-1.amazonaws.com:587 \
    --auth LOGIN \
    --auth-password <password> \
    --auth-user <user> \
    -tls
  ```
- Discourse SSO
  - [Official SSO guide](https://meta.discourse.org/t/official-single-sign-on-for-discourse-sso/13045)
  - Django / Python SSO example
    ```python3
    @login_required
    @verified_email_required
    def discourse_sso(request):
        # https://meta.discourse.org/t/official-single-sign-on-for-discourse-sso/13045
        payload = request.GET.get('sso')
        signature = request.GET.get('sig')

        if None in [payload, signature]:
            return HttpResponseBadRequest('No SSO payload or signature. Please contact support if this problem persists.')

        # Validate the payload
        payload = bytes(parse.unquote(payload), encoding='utf-8')
        decoded = base64.decodebytes(payload).decode('utf-8')
        if len(payload) == 0 or 'nonce' not in decoded:
            return HttpResponseBadRequest('Invalid payload. Please contact support if this problem persists.')

        # Validate the signature: ensure that HMAC-SHA256 of sso_secret, PAYLOAD is equal to the sig
        key = bytes(settings.DISCOURSE_SSO_SECRET, encoding='utf-8')
        h = hmac.new(key, payload, digestmod=hashlib.sha256)
        this_signature = h.hexdigest()

        if not hmac.compare_digest(this_signature, signature):
            return HttpResponseBadRequest('Invalid payload. Please contact support if this problem persists.')

        # Build the return payload
        qs = parse.parse_qs(decoded)
        user = request.user
        def boolean_to_str(b): return str(b).lower()
        # https://github.com/discourse/discourse/blob/master/spec/models/discourse_single_sign_on_spec.rb
        params = {
            'nonce': qs['nonce'][0],
            'external_id': user.id,
            'username': user.username,
            'email': user.email,
            'moderator': boolean_to_str(user.is_staff),
            'admin': boolean_to_str(user.is_superuser),
            'name': user.get_full_name(),
        }
        print(params)

        return_payload = base64.encodebytes(
            bytes(parse.urlencode(params), 'utf-8'))
        h = hmac.new(key, return_payload, digestmod=hashlib.sha256)
        query_string = parse.urlencode(
            {'sso': return_payload, 'sig': h.hexdigest()})

        # Redirect back to Discourse
        discourse_sso_url = f'{settings.DISCOURSE_BASE_URL}/session/sso_login?{query_string}'
        # logger.warning("discourse redirect url: %s", discourse_sso_url)
        return HttpResponseRedirect(discourse_sso_url)
    ```
- [`git pull` a force updated branch](https://stackoverflow.com/questions/9813816/git-pull-after-forced-update)

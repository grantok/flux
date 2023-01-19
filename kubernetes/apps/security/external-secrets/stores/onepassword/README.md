For secrets:
  sources from https://my.1password.com/integrations/active
    token is copied
    1password-credentials.json is base64 encoded....
    cat 1password-credentials.json | base64 | \
  tr '/+' '_-' | tr -d '=' | tr -d '\n' > op-session

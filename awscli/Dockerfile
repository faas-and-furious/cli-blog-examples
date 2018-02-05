FROM python:2.7.14-alpine3.7
# Use any image as your base image, or "scratch"
# Add fwatchdog binary via https://github.com/openfaas/faas/releases/
# Then set fprocess to the process you want to invoke per request - i.e. "cat" or "my_binary"

ADD https://github.com/openfaas/faas/releases/download/0.6.9/fwatchdog /usr/bin
RUN chmod +x /usr/bin/fwatchdog

RUN pip install awscli --upgrade --user
RUN apk add --no-cache less groff

# Populate example here - i.e. "cat", "sha512sum" or "node index.js"

ENV PATH=$PATH:/root/.local/bin/

ENV fprocess="xargs aws"

HEALTHCHECK --interval=5s CMD [ -e /tmp/.lock ] || exit 1
CMD [ "fwatchdog" ]

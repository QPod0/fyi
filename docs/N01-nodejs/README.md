# NodeJS

Refer to: https://nodejs.org/en/download/current

```bash
install_tar_gz()  { curl -o /tmp/TMP.tgz -sL $1 && tar -C /opt/ -xzf /tmp/TMP.tgz $2 && rm /tmp/TMP.tgz ; }

# NODEJS_VERSION_MAJOR="v21" && grep "v${NODEJS_VERSION_MAJOR}."
   ARCH="x64" \
&& NODEJS_VERSION=$(curl -sL https://github.com/nodejs/node/releases.atom | grep 'releases/tag' | head -1 | grep -Po '\d[.\d]+') \
&& NODEJS_VERSION_MAJOR=$(echo "${NODEJS_VERSION}" | cut -d '.' -f1 ) \
&& NODEJS_URL="https://nodejs.org/download/release/latest-v${NODEJS_VERSION_MAJOR}.x/node-v${NODEJS_VERSION}-linux-${ARCH}.tar.gz" \
&& echo "Downloading NodeJS from: ${NODEJS_URL}" \
&& install_tar_gz ${NODEJS_URL} \
&& mv /opt/node* /opt/node \
&& echo  "PATH=/opt/node/bin:$PATH" >> /etc/bash.bashrc \
&& export PATH=/opt/node/bin:$PATH \
&& npm install -g npm \
&& corepack enable \
&& echo "@ Version of Node and npm $(node -v) $(npm -v)"
```

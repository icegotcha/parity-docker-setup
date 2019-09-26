# Build with selected parity version
ARG PARITY_VERSION=${PARITY_VERSION}
FROM parity/parity:${PARITY_VERSION}

ARG NETWORK_NAME=${NETWORK_NAME}
ARG ID=${ID}

USER root
# CrEATE & GIVE PERMISSION IN /parity/config
RUN mkdir -p /parity/config
RUN chown -R parity: /parity/config

# COPY PRIVATE KEYS & PASSWORD FILE
COPY --chown=parity ./parity/authorities/authority${ID}.json /home/parity/.local/share/io.parity.ethereum/keys/${NETWORK_NAME}/authority.json
COPY --chown=parity ./parity/authorities/authority${ID}.pwd /parity/authority.pwd

# COPY NETWORK KEYS
COPY --chown=parity ./parity/networks/node${ID}.network.key /home/parity/.local/share/io.parity.ethereum/network/key

# CREATE DB FILE
RUN mkdir -p /home/parity/.local/share/io.parity.ethereum/chains/${NETWORK_NAME}/db
RUN chown -R parity: /home/parity/.local/share/io.parity.ethereum

# SWITCH USER TO `parity`
USER parity

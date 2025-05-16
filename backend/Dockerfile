# syntax=docker/dockerfile:1.4
FROM directus/directus:11.7.2
USER root
RUN corepack enable \
&& corepack prepare pnpm@8.7.6 --activate \
&& chown node:node /directus
EXPOSE 8055
USER node
CMD : \
&& node /directus/cli.js bootstrap \
&& node /directus/cli.js start;
RUN pnpm install directus-extension-flow-manager@1.4.7
RUN pnpm install directus-extension-grid-layout@1.1.2
RUN pnpm install directus-extension-schema-management-module@2.0.1
RUN pnpm install directus-extension-inline-form-interface@1.2.0
RUN pnpm install @directus-labs/ai-image-generation-operation@1.0.2
RUN pnpm install @directus-labs/experimental-m2a-interface@1.1.0
RUN pnpm install @directus-labs/super-header-interface@1.1.1
RUN pnpm install @directus-labs/inline-repeater-interface@1.0.0
RUN pnpm install @directus-labs/seo-plugin@1.0.1
RUN pnpm install directus-extension-wpslug-interface@1.1.0
RUN pnpm install @directus-labs/ai-writer-operation@1.4.0
RUN pnpm install @directus-labs/card-select-interfaces@1.0.0
RUN pnpm install @directus-labs/simple-list-interface@1.0.0
RUN pnpm install @directus-labs/command-palette-module@1.1.0
RUN pnpm install directus-extension-group-tabs-interface@2.1.0
RUN pnpm install @directus-labs/liquidjs-operation@1.1.0
RUN pnpm install directus-extension-editable-layout@1.1.1

# Copy the assets folder into the container
# USER root
# RUN mkdir -p /directus/data/assets && chown node:node /directus/data/assets
# COPY --chown=node:node ./assets /directus/data/assets

# Copy the extensions folder into the container
# COPY --chown=node:node ./extensions /directus/extensions

# example to copy a custom extension
# RUN pnpm install --dir /directus/extensions/directus-extension-endpoint-geospatial --dev \
#  && pnpm --dir /directus/extensions/directus-extension-endpoint-geospatial run build \
#  && pnpm --dir /directus/extensions/directus-extension-endpoint-geospatial prune --prod
 
# Check if the extsion was compiled
# RUN ls -la /directus/extensions/directus-extension-endpoint-geospatial/dist


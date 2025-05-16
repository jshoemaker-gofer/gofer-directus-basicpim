# Explicitly specify a Directus version to use on Railway
FROM directus/directus:11.6

USER root

# Set the environment variable for your timezone if needed
# RUN apk add --no-cache tzdata
# ENV TZ=America/New_York

RUN npm install -g pnpm --force

USER node

# Installing contributed/custom extensions through npm on Railway
RUN pnpm install directus-extension-computed-interface && pnpm install directus-extension-upsert && \
pnpm install directus-extension-wpslug-interface && pnpm install pg && \
pnpm install directus-extension-flexible-editor && pnpm install @directus-labs/simple-list-interface && \
pnpm install @directus-labs/migration-bundle
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


# Migrations and Directus schema update
RUN npx directus bootstrap
# Copying the extensions, templates, migrations, and snapshots to the Directus container
COPY ./extensions /directus/extensions
COPY ./templates /directus/templates
COPY ./migrations /directus/migrations
COPY ./snapshots /directus/snapshots
COPY ./config.cjs /directus/config.cjs           

# Custom entrypoint script to run Directus on Railway for migrations, snapshots, and extensions
COPY entrypoint.sh /directus/entrypoint.sh
WORKDIR /directus
USER root
RUN chmod +x ./entrypoint.sh
USER node
ENTRYPOINT ["./entrypoint.sh"]
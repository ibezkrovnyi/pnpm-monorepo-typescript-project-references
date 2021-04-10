# pnpm-monorepo-typescript-project-references

## Used

- [x] pnpm workspaces (monorepo)
- [x] typescript project references
      (option 3 from the list below, based on [pnpm](https://pnpm.io/))

## Theory

Theoretically - I wasn't able to find any info on this - project references could be used in the following modes:

1. simple repository (w/ single project), project references are used to split large codebase into smaller pieces
   - imports are relative (inside 'components' subproject: `import foo from '../utilities'`, where utilities is also subproject) (no changes)
   - tried this with one of the legacy projects, actually it was hard to split source code even by root level folders. I found a lot of circlar dependencies, and there is no way to describe circular dependencies in terms of "references" (pls let me know if this statement should be corrected)
2. monorepository, no linking (lerna)

   - path aliases (compilerOptions#paths) are required in all projects
   - imports are modular (`import foo from 'module'`) or relative, however making imports relative might lead to declarationMap issues in the published npm packages
   - not sure if it is good approach, bcs there is no way to test dependent projects in the dependency tree order

3. monorepository, linking (lerna, yarn workspaces)
   - path aliases are not needed
   - imports are modular (`import foo from 'module'`)

## Refs

- https://shopify.engineering/migrating-large-typescript-codebases-project-references
- https://ebaytech.berlin/optimizing-multi-package-apps-with-typescript-project-references-d5c57a3b4440

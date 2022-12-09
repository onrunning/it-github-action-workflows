  <!-- build_push_ecr:
    uses: onrunning/it-github-action-workflows/.github/workflows/build_push_image.yaml@main
    with:
      repository: <ecr-repository-name>
      environment: development
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
     
  deploy-staging:
    needs: [build_push_ecr]
    uses: onrunning/it-github-action-workflows/.github/workflows/deploy_argocd.yaml@main
    with:
       image-tag: ${{ needs.build_push_ecr.outputs.tag }}
       ecr_repository: <ecr-repository>
       file_path: <path-to-argocd-file>
    secrets:
      GITOPS_USER: ${{ secrets.GITOPS_TOKEN }}
      GITOPS_TOKEN: ${{ secrets.GITOPS_TOKEN }} -->

# 🤝 Collaborative Workflow

This document defines how dataset updates, notebook changes, and benchmark revisions are collaboratively managed.

## Workflow Stages
1. Dataset review
2. Annotation update
3. Roboflow version freeze
4. Colab benchmark rerun
5. Metrics validation
6. GitHub documentation update

## Team Rules
- All class changes must update `class_definitions.md`
- Every benchmark run must record dataset version
- README metrics must match notebook outputs
- Use pull requests for structural repo changes

## Review Checklist
- [ ] Dataset version recorded
- [ ] Metrics reproducible
- [ ] Visual evidence uploaded
- [ ] Error analysis updated

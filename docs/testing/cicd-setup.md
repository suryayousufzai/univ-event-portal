# CI/CD Setup Documentation

**Project:** University Event Registration Portal  
**DevOps Engineer:** Gita Rahmany  
**Sprint:** Sprint 1  
**Date:** November 19, 2025

---

## Overview

This document explains how the CI/CD (Continuous Integration and Continuous Deployment) pipeline is set up for our project. The goal is to ensure that our code and documents are tested, organized, and ready for merging into the main branch smoothly.

---

## Version Control

**Platform:** GitHub  
**Repository:** https://github.com/suryayousufzai/univ-event-portal

### Branching & Workflow

- main  
- Personal branches (one per teammate)  
- All changes are merged into main via pull requests

### Folder-Based Organization

```
main/
 ├── backend/
 ├── frontend/
 ├── docs/
 │     ├── testing/
 │     ├── sprint-backlogs/
 │     ├── backlog/
 │     ├── design/
 │     ├── meeting-minutes/
 │     ├── sequence-diagrams/
 │     ├── stand-up/
 │     └── use-cases/
 └── recording/
```

---

## GitHub Actions Workflow

**File Location:** `.github/workflows/ci.yml`

---

## Automated Testing

**Test Framework:** Jest  
**Coverage Target:** 80%  
**Runs on:** Pull requests to main

- Test files and results are stored in `docs/testing/`

---

## Deployment Strategy

**Environment:** Development  
**Platform:** Local server (production TBD)  
**Deployment:** Manual for Sprint 1; automated deployment will be added in future sprints

---

## Code Quality Tools

- ESLint  
- Prettier  
- SonarQube (planned)

---

## Future Enhancements

- Automated deployment to staging server  
- Integration with Docker  
- Automated security scanning  
- Performance monitoring

---

**Status:** Basic CI/CD setup is completed for Sprint 1



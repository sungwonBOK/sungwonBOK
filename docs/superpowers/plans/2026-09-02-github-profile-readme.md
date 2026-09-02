# GitHub Profile README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a Korean GitHub profile README that introduces two featured projects for a general development club application.

**Architecture:** The root `README.md` is the only public profile artifact. It contains a short introduction, two self-contained project cards using the user's requested pattern, a compact technology section, and direct repository links. Image and demo areas use clear text insertion points rather than fabricated assets or URLs.

**Tech Stack:** GitHub-flavored Markdown, GitHub profile README.

**Spec:** `docs/superpowers/specs/2026-09-02-github-profile-design.md`

## Global Constraints

- Use Korean copy and verified public repository URLs.
- Include only RestructuringHome and the third-person combat futsal game as featured projects.
- Describe FutsalGame as MVP work and do not claim unverified live Internet multiplayer proof.
- Do not invent a GIF/image or demo-video URL.
- Keep each project's `담당` limited to the implementation scope described in the profile.

---

### Task 1: Write the profile README

**Files:**
- Create: `README.md`
- Test: rendered GitHub-flavored Markdown review and `git diff --check`

**Interfaces:**
- Consumes: the design spec and public repository URLs.
- Produces: the root-level `README.md` required for GitHub profile rendering.

- [ ] **Step 1: Create the profile structure and introduction**

  Create `README.md` with this introduction and section heading:

  ```markdown
  # 안녕하세요, 복성원입니다. 👋

  사용자에게 실제로 도움이 되는 경험을 만들고, 그 경험을 뒷받침하는 구현 문제를 해결하는 개발자입니다.

  ## Featured Projects
  ```

- [ ] **Step 2: Add the RestructuringHome project card**

  Add this project card below the featured-project heading:

  ```markdown
  ### 🏠 RestructuringHome - 직접 설계하는 우리 집 공간

  _대표 GIF 또는 이미지 추가 예정_

  React Native / Expo / TypeScript / Supabase

  사용자가 방 평면도를 직접 만들고 가구를 배치해 더 나은 공간 구성을 탐색할 수 있는 모바일 앱입니다.

  - 주요 구현: 방 평면도 생성, 가구 추가·이동·크기 조절·회전, 저장 및 불러오기
  - 개발 인원: 개인 프로젝트
  - 담당: 방 평면도 편집 경험과 가구 편집 기능 구현

  → [GitHub Repository](https://github.com/sungwonBOK/ResturucturingHome)
  → Demo Video (추가 예정)
  ```

- [ ] **Step 3: Add the futsal-game project card in the requested format**

  Add this project card after RestructuringHome:

  ```markdown
  ### ⚽ 프로젝트명 - 3인칭 격투 풋살 게임

  _대표 GIF 또는 이미지 추가 예정_

  Unity / C# / Multiplayer

  축구와 격투 요소를 결합한 3인칭 멀티플레이 게임입니다. 현재 MVP 단계로 캐릭터 조작, 패스·슛, 격투 시스템, 멀티플레이 기능을 구현했습니다.

  - 주요 구현: 캐릭터 조작, 패스/슛, 격투 시스템, 멀티플레이
  - 개발 인원: 2명
  - 담당: 게임플레이 상호작용과 P2P 멀티플레이 동기화 구현

  → [GitHub Repository](https://github.com/sungwonBOK/FutsalGame)
  → Demo Video (추가 예정)
  ```

- [ ] **Step 4: Add compact technologies and contact information**

  Append:

  ```markdown
  ## Tech

`TypeScript` `React Native` `Expo` `Supabase` `Unity` `C#` `Multiplayer`

## Contact

[GitHub](https://github.com/sungwonBOK)
  ```

- [ ] **Step 5: Verify Markdown quality**

  Run:

  ```powershell
  git diff --check
  git status --short
  ```

  Expected: no whitespace errors and one untracked `README.md`.

- [ ] **Step 6: Commit the rendered profile source**

  Run:

  ```powershell
  git add README.md
  git commit -m "feat: add GitHub profile README"
  ```

### Task 2: Publish and verify the profile README

**Files:**
- Modify: `README.md` (commit only; no content changes expected)
- Test: GitHub README API response and remote branch verification

**Interfaces:**
- Consumes: committed root `README.md` from Task 1.
- Produces: a public profile README visible at `https://github.com/sungwonBOK`.

- [ ] **Step 1: Push the profile README**

  Run:

  ```powershell
  git push origin master
  ```

- [ ] **Step 2: Verify GitHub serves the README from the profile repository**

  Run:

  ```powershell
  & 'C:\Program Files\GitHub CLI\gh.exe' api repos/sungwonBOK/sungwonBOK/readme --jq .html_url
  git ls-remote origin refs/heads/master
  ```

  Expected: a README URL under `sungwonBOK/sungwonBOK` and a remote `master` SHA matching local `HEAD`.

# security-audit-skill: peraturan untuk Claude Code

## CI/CD: runner syarikat sahaja

- **Jangan sekali-kali guna runner GitHub** (`ubuntu-latest`, `ubuntu-*`, `macos-*`, `windows-*`) dalam mana-mana aliran kerja GitHub Actions repo ini. Hanya runner syarikat (self-hosted).
- Setiap job: `runs-on: ${{ fromJSON(vars.RUNNER_LABELS || '["self-hosted","linux","x64"]') }}`. Jangan jadikan runner GitHub sebagai lalai atau sandaran.
- Jangan anggap alat seperti `gh`, `jq`, Docker atau Android SDK wujud pada runner: semak dan pasang dalam langkah aliran kerja, atau elak.
- Jika terjumpa aliran kerja yang guna runner GitHub, maklumkan dan tukar ke runner syarikat sebelum ia dijalankan.
- **Runner `barite` dikhaskan untuk `EARTH-Info/earthid` sahaja.** Repo ini tidak boleh menggunakannya. Label `self-hosted, linux, x64` juga padan dengan `barite`, jadi jangan anggap label itu cukup: pastikan `barite` diasingkan dalam runner group khas earthid, atau guna label khas runner yang dibenarkan.

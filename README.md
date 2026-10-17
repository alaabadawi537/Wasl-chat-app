
      - name: Build APK
        run: |
          cd "$PROJECT_DIR"
          set -o pipefail
          flutter build apk --debug --verbose 2>&1 | tee build.log

      - name: Upload build log
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: wasl-build-log
          path: /tmp/wasl/wasl_chat_mvp/build.log
          if-no-files-found: ignore

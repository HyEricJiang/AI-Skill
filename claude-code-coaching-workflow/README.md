# Claude Code 月度教練分析組合包

這個資料夾可直接分享給使用 Claude Code 的同仁。它會把一位同仁的「當月改變表格」與「教練逐字稿」整理成有證據、可行動、可追蹤的月度教練分析。

## 這一包會產出什麼

每次分析固定包含：

1. 本月事件摘要
2. 當月工作狀態
3. 慣性模式（只寫有證據的教練假設）
4. 好的行為／思考與可複製做法
5. 一至三個下一步與驗證方式
6. 下次教練可追問
7. 可回填表格摘要
8. 品質檢核報告

## 第一次使用

1. 將整個資料夾複製到自己的電腦。
2. 在終端機進入此資料夾後啟動 Claude Code：

   ```bash
   cd claude-code-coaching-workflow
   claude
   ```

3. 複製兩份空白模板：
   - `templates/monthly-change-table-template.md`
   - `templates/transcript-template.md`
4. 填妥後，分別放入：
   - `inputs/monthly-change-tables/`
   - `inputs/transcripts/`
5. 在 Claude Code 輸入：

   ```text
   /monthly-coaching-analysis 王小明 2026-07
   ```

6. Claude 完成後，先閱讀 `outputs/monthly-analysis/` 中的分析，再確認同資料夾內的 validation report 是否通過。

## 建議檔名

```text
inputs/monthly-change-tables/{姓名}-{YYYY-MM}.md
inputs/transcripts/{姓名}-{YYYY-MM}.txt
outputs/monthly-analysis/{姓名}_{YYYY-MM}_月度教練分析.md
outputs/monthly-analysis/{姓名}_{YYYY-MM}_validation.md
```

若原始檔名不同也可以使用，但必須在執行指令時提供完整路徑，並由 Claude 先確認兩份資料的姓名與月份一致。

## 可直接對 Claude 說的話

標準分析：

```text
/monthly-coaching-analysis 王小明 2026-07
```

指定來源：

```text
請執行月度教練分析。對象是王小明，月份是 2026-07。
表格在 inputs/monthly-change-tables/王小明-2026-07.md，
逐字稿在 inputs/transcripts/王小明-2026-07.txt。
```

批次分析：

```text
請先建立本月來源對照表，再逐人執行月度教練分析。
每一位都要封閉分析並做交叉污染檢查；任何姓名、月份或來源衝突都先停止該份輸出。
```

## 資料安全

- 不要把真實資料提交到公開 Git 儲存庫。
- 分享組合包前，保留模板與合成範例即可，不要附上真實輸入或輸出。
- 不在分析稿中貼出完整逐字稿、私人 Email、電話、客戶機密或不必要的個資。
- 若資料不完整或互相衝突，標記「來源需確認」，不要猜測。

## 本版範圍

這一版涵蓋「表格＋逐字稿 → 月度教練分析 Markdown＋檢核報告」的檔案式流程，不會寄信、不會寫回 Google Sheet，也不會上傳 Google Drive。若未來需要上述整合，應另行設定權限、收件人核對、dry-run 與人工覆核機制。

## 主要檔案

- `CLAUDE.md`：Claude Code 每次開啟專案都會讀取的核心規則。
- `.claude/skills/monthly-coaching-analysis/SKILL.md`：可用 `/monthly-coaching-analysis` 呼叫的完整工作流。
- `.claude/skills/monthly-coaching-analysis/references/`：分析準則、輸出格式與檢核表。
- `templates/`：可以直接複製填寫的輸入模板。
- `examples/synthetic-example/`：不含真實同仁資料的合成範例。


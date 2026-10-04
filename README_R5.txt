Junba AI Transcriber v3.8.2 APK R5
==================================

這一版不是再次猜測原因，而是依 R4.1 實機抓到的完整 stack trace 修正：

java.lang.NullPointerException
Attempt to invoke ScrollBarDrawable.mutate() on a null object reference
at android.view.View.onDrawScrollBars(...)

測試裝置：vivo V2413 / Android 16 (SDK 36) / arm64-v8a

R5 修正：
1. 移除 result.setScrollbarFadingEnabled(false)。
2. FullTranscriberActivity 所有主要 ScrollView 關閉「可視 scrollbar」，但保留手指上下滑動。
3. 逐字稿 EditText 關閉 vertical/horizontal scrollbar 與 overscroll，但仍可手指捲動、編輯、最前/最後跳轉。
4. 主 Launcher 改成無 ScrollView 的極簡安全殼，啟動後自動開完整轉錄功能。
5. 完整轉錄功能仍放在 :full_transcriber 獨立程序；若未來 engine 發生 crash，安全殼仍可保留診斷。
6. 保留 Gemini Files API、長音訊策略、Whisper、Hybrid、API Key 收折、進度、時間序、日期/時間資料夾存檔。
7. Windows 版完全未修改。

GitHub Actions：Build Junba Android APK v3.8.2 R5
Artifact：Junba-v382-APK-R5
APK：Junba-R5.apk

建議測試：
- 先完整解除安裝舊診斷版，再安裝 R5。
- 點 App 後應短暫看到 R5 安全啟動頁，隨即自動進入完整轉錄介面。
- 先停留 20 秒確認不閃退，再測 Gemini Key、短音檔、Whisper、Hybrid、長音訊、存檔。

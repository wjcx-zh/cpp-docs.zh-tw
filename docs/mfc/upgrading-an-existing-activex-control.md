---
title: 升級現有的 ActiveX 控制項
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
ms.openlocfilehash: 06c39240d3718f6fbaa15b46abeb8ac9132b5945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510871"
---
# <a name="upgrading-an-existing-activex-control"></a>升級現有的 ActiveX 控制項

現有的 ActiveX 控制項 (先前稱為 OLE 控制項) 可以在網際網路上使用, 而不需要修改。 不過, 您可能會想要修改控制項來改善其效能。

> [!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊, 請參閱[ActiveX 控制項](activex-controls.md)。

當您在網頁上使用控制項時, 還有其他考慮。 .Ocx 檔案和所有支援的檔案都必須在目的電腦上, 或透過網際網路下載。 這會讓程式碼大小和下載時間成為重要的考慮。 下載可以封裝在帶正負號的 .cab 檔案中。 您可以將控制項標示為安全進行腳本處理, 並以安全的方式進行初始化。

本文討論下列主題：

- [封裝要下載的程式碼](#_core_packaging_code_for_downloading)

- [將控制項標示為可安全編寫腳本和初始化](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [授權問題](#_core_licensing_issues)

- [簽署程式碼](#_core_signing_code)

- [管理調色板](#_core_managing_the_palette)

- [Internet Explorer 瀏覽器安全性層級和控制行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

您也可以新增 [優化], 如[ActiveX 控制項中所述:優化](../mfc/mfc-activex-controls-optimization.md)。 您可以使用標記來非同步下載屬性和大型 Blob, 如[網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)中所述。

##  <a name="_core_packaging_code_for_downloading"></a>封裝要下載的程式碼

如需這個主題的詳細資訊, 請參閱[封裝 ActiveX 控制項](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29)。

### <a name="the-codebase-tag"></a>CODEBASE 標記

ActiveX 控制項是使用`<OBJECT>`標記內嵌在網頁中。 `<OBJECT>`標記的參數會指定要從中下載控制項的位置。 `CODEBASE` `CODEBASE`可以成功指向數種不同的檔案類型。

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>搭配 OCX 檔案使用 CODEBASE 標記

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

此解決方案只會下載控制項的 .ocx 檔案, 而且需要有任何支援的 Dll 已安裝在用戶端電腦上。 這適用于以視覺C++效果建立的 internet EXPLORER 和 MFC ActiveX 控制項, 因為 internet Explorer 隨附視覺C++控制項的支援 dll。 如果另一個具有 ActiveX 控制項功能的網際網路瀏覽器用來觀看此控制項, 此方案將無法使用。

### <a name="using-the-codebase-tag-with-an-inf-file"></a>搭配使用程式碼基底標記與 INF 檔案

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

.Inf 檔案將控制 .ocx 和其支援檔案的安裝。 不建議使用這個方法, 因為您無法簽署 .inf 檔案 (請參閱在程式碼簽署上的指標的[簽署程式碼](#_core_signing_code))。

### <a name="using-the-codebase-tag-with-a-cab-file"></a>搭配使用程式碼基底標記與 CAB 檔案

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

封包檔是封裝使用 MFC 之 ActiveX 控制項的建議方式。 封裝封包檔中的 MFC ActiveX 控制項可讓您包含 .inf 檔案, 以控制 ActiveX 控制項和任何相依 Dll (例如 MFC Dll) 的安裝。 使用 CAB 檔案會自動壓縮程式碼, 以便更快速地下載。 如果您使用 .cab 檔案進行元件下載, 則簽署整個 .cab 檔案的速度會比每個個別元件更快。

### <a name="creating-cab-files"></a>建立 CAB 檔案

建立封包檔的工具現在是[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)的一部分。

所指向的封包檔`CODEBASE`應該包含您的 ActiveX 控制項的 .ocx 檔案, 以及用來控制其安裝的 .inf 檔。 您可以藉由指定控制檔的名稱和 .inf 檔案來建立封包檔。 請勿包含可能已存在於此封包檔中之系統上的相依 Dll。 例如, MFC Dll 會封裝在個別的封包檔中, 並由控制 .inf 檔案所參考。

如需如何建立 CAB 檔案的詳細資訊, 請參閱[建立](/windows/win32/devnotes/cabinet-api-functions)封包檔。

### <a name="the-inf-file"></a>INF 檔案

下列 spindial 範例會列出支援的檔案, 以及 MFC Spindial 控制項所需的版本資訊。 請注意, MFC Dll 的位置是 Microsoft 網站。 Mfc42 是由 Microsoft 提供和簽署。

```
Contents of spindial.inf:
[mfc42installer]
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0
```

### <a name="the-object-tag"></a>\<物件 > 標記

下列範例說明如何使用`<OBJECT>`標記來封裝 MFC Spindial 範例控制項。

```
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">
<PARAM NAME="_Version" VALUE="65536">
<PARAM NAME="_ExtentX" VALUE="2646">
<PARAM NAME="_ExtentY" VALUE="1323">
<PARAM NAME="_StockProps" VALUE="0">
<PARAM NAME="NeedlePosition" VALUE="2">
</OBJECT>
```

在此情況下, spindial 會包含兩個檔案: spindial 和 spindial。 下列命令會建立封包檔:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144`參數會在封包中保留空間以進行程式碼簽署。

### <a name="the-version-tag"></a>版本戳記

請注意, 使用`#Version` CAB 檔案指定的資訊會套用至`<OBJECT>`標記的*CLASSID*參數所指定的控制項。

視指定的版本而定, 您可以強制下載您的控制項。 如需包含程式`OBJECT` *代碼基*底參數之標記的完整規格, 請參閱 W3C 參考。

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>將控制項標示為可安全編寫腳本和初始化

在網頁中使用的 ActiveX 控制項應標示為安全的腳本, 並可安全地進行初始化 (如果它們實際上是安全的)。 安全控制項不會執行磁片 IO, 或直接存取電腦的記憶體或暫存器。

控制項可以標示為安全的腳本, 並可透過登錄安全地進行初始化。 修改`DllRegisterServer`以加入類似下列的專案, 將控制項標示為安全, 以便在登錄中進行腳本和持續性。 另一種方法是執行`IObjectSafety`。

您將為控制項定義 Guid (全域唯一識別碼), 將它標示為安全的腳本處理和持續性。 可以安全編寫腳本的控制項將包含類似下列的登錄專案:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

可以安全地從持續性資料初始化的控制項, 會標示為具有類似下列登錄專案的持續性:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

新增類似下列的專案 (以`{06889605-B8D0-101A-91F1-00608CEAD5B3}`控制項的類別識別碼取代), 將您的金鑰與下列類別識別碼建立關聯:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a>授權問題

如果您想要在網頁上使用授權的控制項, 您必須確認授權合約允許其在網際網路上使用, 並為其建立授權套件檔案 (LPK)。

如果執行 Internet Explorer 的電腦未獲授權使用該控制項, 授權的 ActiveX 控制項將無法在 HTML 網頁中正確載入。 例如, 如果授權控制項是使用視覺效果C++所建立, 則使用控制項的 HTML 網頁將會在建立控制項的電腦上正確載入, 但除非包含授權資訊, 否則不會載入到其他電腦上。

若要在 Internet Explorer 中使用已授權的 ActiveX 控制項, 您必須檢查廠商的授權合約, 確認該控制項的授權允許:

- 轉散發

- 在網際網路上使用控制項

- 使用 Codebase 參數

若要在 nonlicensed 電腦的 HTML 網頁中使用授權的控制項, 您必須產生授權封裝檔案 (LPK)。 LPK 檔案包含 HTML 網頁中授權控制項的執行時間授權。 此檔案是透過 LPK_TOOL 所產生。隨附于 ActiveX SDK 的 EXE。

#### <a name="to-create-an-lpk-file"></a>若要建立 LPK 檔案

1. 執行 LPK_TOOL。在授權使用控制項的電腦上的 EXE。

1. 在 [**授權套件撰寫工具**] 對話方塊的 [**可用的控制項**] 清單方塊中, 選取要在 HTML 頁面上使用的每個授權 ActiveX 控制項, 然後按一下 [**新增**]。

1. 按一下 **儲存 &** 結束, 然後輸入 LPK 檔案的名稱。 這會建立 LPK 檔案並關閉應用程式。

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>在 HTML 頁面上內嵌授權的控制項

1. 編輯您的 HTML 網頁。 在 [HTML] 頁面中, \<將 [授權管理員] 物件的物件 > 標籤\<插入至任何其他物件 > 標記之前。 授權管理員是一種與 Internet Explorer 一起安裝的 ActiveX 控制項。 其類別識別碼如下所示。 將授權管理員物件的 LPKPath 屬性設定為 LPK 檔案的路徑和名稱。 每個 HTML 頁面只能有一個 LPK 檔案。

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. 在 [授權管理員] 標籤之後, 為授權的控制項插入物件>標記。\<

   例如, 顯示 Microsoft 遮罩編輯控制項的 HTML 頁面如下所示。 第一個類別識別碼是用於授權管理員控制項, 第二個類別識別碼是用於遮罩編輯控制項。 將標籤變更為指向您稍早建立之 .lpk 檔案的相對路徑, 並新增物件標記, 包括控制項的類別 ID。

1. 如果使用\<NCompass ActiveX 外掛程式, 請插入您的 LPK 檔案的內嵌 > 屬性。

   如果您的控制項可以在其他啟用作用中的瀏覽器上查看 (例如, 使用 NCompass ActiveX 外掛程式的 Netscape), 您必須\<新增內嵌 > 語法, 如下所示。

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

如需控制授權的詳細資訊, [請參閱 ActiveX 控制項:授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

##  <a name="_core_signing_code"></a>簽署程式碼

程式碼簽署是設計用來識別程式碼的來源, 並確保程式碼在簽署之後不會變更。 視瀏覽器的安全性設定而定, 可能會在下載程式代碼之前警告使用者。 使用者可以選擇信任特定的憑證擁有者或公司, 在此情況下, 將會下載受信任的程式碼而不發出警告。 程式碼經過數位簽署, 以避免遭到篡改。

請確定您的最終程式碼已簽署, 讓您的控制項可以自動下載, 而不會顯示信任警告訊息。 如需如何簽署程式碼的詳細資訊, 請參閱 ActiveX SDK 中有關 Authenticode 的檔, 並參閱[簽署 CAB](/windows/win32/devnotes/cabinet-api-functions)檔案。

視信任和瀏覽器的安全性層級設定而定, 可能會顯示憑證以識別簽署人員或公司。 如果安全性層級為 [無], 或已簽署控制項的憑證擁有者是受信任的, 則不會顯示憑證。 如需瀏覽器安全性設定如何判斷您的控制項是否已下載並顯示憑證的詳細資訊, 請參閱[Internet Explorer 瀏覽器安全性層級和控制項行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)。

數位簽章保證程式碼經過簽署後, 尚未變更。 程式碼的雜湊會被採用, 並內嵌在憑證中。 此雜湊稍後會與在程式碼下載後但執行之前所建立的程式碼雜湊進行比較。 Verisign 之類的公司可以提供簽署程式碼所需的私用金鑰和公開金鑰。 ActiveX SDK 隨附 MakeCert, 這是用來建立測試憑證的公用程式。

##  <a name="_core_managing_the_palette"></a>管理調色板

容器會決定調色板, 並將其提供為環境屬性**DISPID_AMBIENT_PALETTE**。 容器 (例如 Internet Explorer) 會選擇頁面上所有 ActiveX 控制項所使用的調色板, 以判斷自己的調色板。 這可避免顯示閃爍, 並顯示一致的外觀。

控制項可以覆寫`OnAmbientPropertyChange`以處理對調色板的變更通知。

控制項可以覆寫`OnGetColorSet` , 以傳回用來繪製調色板的色彩集。 容器會使用傳回值來判斷控制項是否為調色板感知。

在 OCX 96 指導方針底下, 控制項必須一律在背景中實現其調色板。

不使用環境調色板屬性的舊版容器會傳送 WM_QUERYNEWPALETTE 和 WM_PALETTECHANGED 訊息。 控制項可以覆寫`OnQueryNewPalette`和`OnPaletteChanged`以處理這些訊息。

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Internet Explorer 瀏覽器安全性層級和控制行為

瀏覽器具有安全性層級的選項, 可由使用者進行設定。 由於網頁可包含可能會危害使用者電腦的活動內容, 因此瀏覽器允許使用者選取安全性層級的選項。 視瀏覽器執行安全層級的方式而定, 可能完全不會下載控制項, 或是會顯示憑證或警告訊息, 讓使用者在執行時間選擇是否要下載控制項。 在 Internet Explorer 上, [高]、[中] 和 [低] 安全性層級下 ActiveX 控制項的行為如下所示。

### <a name="high-safety-mode"></a>高安全性模式

- 不會下載未簽署的控制項。

- 如果未受信任, 已簽署的控制項將會顯示憑證 (使用者可以選擇一律信任來自此憑證擁有者的程式碼, 從現在開始)。

- 只有標示為 safe 的控制項才會有持續性資料和/或可編寫腳本。

### <a name="medium-safety-mode"></a>中安全性模式

- 未簽署的控制項在下載前會顯示警告。

- 已簽署的控制項將會顯示憑證 (如果未受信任)。

- 未標示為安全的控制項將會顯示警告。

### <a name="low-safety-mode"></a>低安全性模式

- 下載控制項而不發出警告。

- 腳本和持續性會在沒有警告的情況下發生。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC ActiveX 控制項：授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

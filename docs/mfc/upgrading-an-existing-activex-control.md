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
ms.openlocfilehash: fc7313c862d3536326894c947fa371d833e8fab8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180755"
---
# <a name="upgrading-an-existing-activex-control"></a>升級現有的 ActiveX 控制項

現有的 ActiveX 控制項 （先前稱為 OLE 控制項） 可以不需修改網際網路上使用。 不過，您可能想要修改控制項，以提升其效能。

> [!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

當使用您在網頁上的控制項，還有其他考量。 .Ocx 檔案和所有支援的檔案必須是目標電腦上，或透過網際網路下載。 這可讓程式碼大小和下載時間很重要的考量。 下載項目可以封裝在簽署的.cab 檔案中。 您可以標示為安全的指令碼，以及用於初始化安全控制項。

本文討論下列主題：

- [下載的程式碼封裝](#_core_packaging_code_for_downloading)

- [標示指令碼，並初始化控制項的安全](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [授權問題](#_core_licensing_issues)

- [簽署程式碼](#_core_signing_code)

- [管理調色盤](#_core_managing_the_palette)

- [Internet Explorer 瀏覽器安全性層級和控制行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

您也可以在中所述新增最佳化， [ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)。 Moniker 可以用來下載內容，和大型 Blob 以非同步方式中所述[網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)。

##  <a name="_core_packaging_code_for_downloading"></a> 下載的程式碼封裝

如需有關這個主題的詳細資訊，請參閱 <<c0> [ 封裝 ActiveX 控制項](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29)。

### <a name="the-codebase-tag"></a>程式碼基底標記

ActiveX 控制項內嵌在網頁使用`<OBJECT>`標記。 `CODEBASE`參數`<OBJECT>`標記會指定要從中下載此控制項的位置。 `CODEBASE` 可以指向幾個不同的檔案類型的成功。

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>使用程式碼基底標記與 OCX 檔案

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

下載只控制項的.ocx 檔案，此解決方案，並需要用戶端電腦上已安裝任何支援的 Dll。 這適用於 Internet Explorer 和 MFC ActiveX 控制項建置具有視覺效果C++，因為 Internet Explorer 隨附視覺效果支援的 DllC++控制項。 如果是 ActiveX 控制項支援的其他網際網路瀏覽器來檢視這個控制項，此解決方案將無法運作。

### <a name="using-the-codebase-tag-with-an-inf-file"></a>使用 INF 檔案的程式碼基底標記

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

.Inf 檔案會控制安裝.ocx 和其支援的檔案。 不建議使用這個方法因為它不是能夠登入.inf 檔案 (請參閱[簽署的程式碼](#_core_signing_code)上程式碼簽署的指標)。

### <a name="using-the-codebase-tag-with-a-cab-file"></a>使用 CAB 檔案的程式碼基底標記

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

封包檔的建議方式是使用 MFC 的封裝 ActiveX 控制項。 封裝的封包檔中的 MFC ActiveX 控制項，可讓.inf 檔案是要用於安裝的 ActiveX 控制項和任何相依的 Dll （例如 MFC Dll) 的控制項。 使用封包檔自動壓縮更快的下載程式碼。 如果您使用的元件下載的.cab 檔案，速度會簽署整個.cab 檔案比每個個別的元件。

### <a name="creating-cab-files"></a>建立 CAB 檔

工具來建立封包檔屬於現在[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。

封包檔所指的`CODEBASE`應包含您的 ActiveX 控制項的.ocx 檔案及控制其安裝.inf 檔案。 您建立封包檔，藉由指定控制檔案的名稱和.inf 檔案。 不包含此封包檔中的系統可能已存在的相依 Dll。 例如，MFC Dll 是封裝在個別的封包檔，而所控制的.inf 檔案參考。

如需有關如何建立封包檔的詳細資訊，請參閱 <<c0> [ 建立封包檔](/windows/desktop/devnotes/cabinet-api-functions)。

### <a name="the-inf-file"></a>INF 檔案

下列範例、 spindial.inf、 清單支援的檔案和版本資訊所需的 MFC Spindial 控制。 請注意 MFC Dll 的位置是 Microsoft 網站。 Mfc42.cab 是提供，並由 Microsoft 簽署。

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

下列範例說明如何使用`<OBJECT>`封裝 MFC Spindial 範例控制項的標記。

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

在此情況下，spindial.cab 將包含兩個檔案、 spindial.ocx 和 spindial.inf。 下列命令會建立封包檔：

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144`參數會保留在程式碼簽署封包中的空間。

### <a name="the-version-tag"></a>版本標記

請注意以下`#Version`CAB 檔案以指定的資訊適用於所指定的控制項*CLASSID*參數`<OBJECT>`標記。

根據指定的版本，您可以強制下載您的控制項。 完整規格`OBJECT`包括標記*程式碼基底*參數，請參閱 W3C 參考。

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> 標示指令碼，並初始化控制項的安全

在網頁中使用的 ActiveX 控制項應該標示為安全用於指令碼和初始化如果它們實際上是安全的。 不安全的控制項將會執行磁碟 IO，或直接存取的記憶體或暫存器的機器。

控制項可以標示為安全用於指令碼和初始化透過登錄中。 修改`DllRegisterServer`新增如下所示將標示為安全的指令碼和登錄中的持續性控制項的項目。 替代方法是實作`IObjectSafety`。

您將為您的控制項，將它標記為安全的指令碼和持續性定義的 Guid （全域唯一識別碼）。 可以安全地編寫指令碼的控制項將會包含類似下列的登錄項目：

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

可以安全地從永續性資料來初始化的控制項是標示為安全的登錄項目類似於使用的持續性的：

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

新增類似以下的項目 (以取代您的控制項類別取代識別碼`{06889605-B8D0-101A-91F1-00608CEAD5B3}`) 將您的金鑰關聯的下列類別識別碼：

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a> 授權問題

如果您想要使用授權的控制項在網頁上，您必須確認授權合約可讓網際網路上的用法，並為其建立的授權封裝檔案 (LPK)。

授權的 ActiveX 控制項將無法正確載入 HTML 網頁中如果執行 Internet Explorer 的電腦未獲授權使用的控制項。 例如，如果已授權的控制項是使用 Visual C++，在其中建立此控制項，但除非已包含授權資訊時，它將不在不同的電腦上載入的電腦上使用控制項的 HTML 頁面會正確載入。

若要在 Internet Explorer 中使用授權的 ActiveX 控制項，您必須檢查供應商授權合約，以確認控制項授權允許：

- 轉散發

- 在網際網路上控制項的使用

- 使用程式碼基底參數

若要使用授權的控制項要在未經授權的電腦上的 HTML 頁面中，您必須產生的授權封裝檔案 (LPK)。 LPK 檔案包含 HTML 網頁中的授權控制項的執行階段授權。 透過 LPK_TOOL 會產生這個檔案。ActiveX SDK 隨附的 EXE。 如需詳細資訊，請參閱 MSDN 網站，網址[ http://msdn.microsoft.com ](http://msdn.microsoft.com)。

#### <a name="to-create-an-lpk-file"></a>若要建立的 LPK 檔案

1. 執行 LPK_TOOL。使用控制項授權的電腦上的 EXE。

1. 在 **授權封裝 Authoring Tool**對話方塊的 **可用的控制項**清單方塊中，選取每個授權的 ActiveX 控制項，將會使用 HTML 網頁上，按一下 **新增**.

1. 按一下 **儲存並結束**輸入 LPK 檔案的名稱。 這會建立 LPK 檔案，並關閉應用程式。

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>若要內嵌在 HTML 網頁上的授權的控制項

1. 編輯 HTML 網頁。 在 [HTML] 頁面中，插入\<物件 > 標記之前的任何其他的授權管理員物件\<物件 > 標記。 授權管理員是已安裝 Internet explorer 的 ActiveX 控制項。 它的類別 ID 如下所示。 授權管理員物件的 LPKPath 屬性設 LPK 檔案的名稱與路徑。 您可以有只有一個的 LPK 檔案，每個 HTML 頁面。

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. 插入\<物件 > 為您授權的控制項，授權管理員標記之後的標記。

   比方說，如下所示，顯示 Microsoft 遮罩編輯控制項的 HTML 網頁。 識別碼為授權管理員控制的第一個類別，識別碼是遮罩編輯控制項的第二個類別。 變更標籤，來指向您在稍早建立的.lpk 檔案的相對路徑，並新增為您的控制項的類別 id 的物件標記。

1. 插入\<內嵌 > 屬性的 LPK 檔案，如果使用 NCompass ActiveX 外掛程式。

   如果您的控制項可能會檢視上其他作用中啟用瀏覽器 — 比方說，使用 NCompass ActiveX 外掛程式的 Netscape — 您必須新增\<內嵌 > 語法，如下所示。

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

如需控制項授權的詳細資訊，請參閱[ActiveX 控制項：授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

##  <a name="_core_signing_code"></a> 簽署程式碼

程式碼簽署設計來識別來源的程式碼，並保證以來尚未變更的程式碼簽署。 根據瀏覽器安全性設定，使用者可能會收到警告之前下載的程式碼。 使用者可以選擇信任特定憑證擁有者或公司，在其中案例的程式碼簽署的那些信任會被下載，而不發出警告。 程式碼是數位簽章以避免遭到竄改。

請確定您最後的程式碼簽署，讓您的控制項可以自動下載但不顯示信任的警告訊息。 如需有關如何簽署程式碼的詳細資訊，請檢查 Authenticode ActiveX SDK 中的文件，並請參閱[簽署的 CAB 檔案](/windows/desktop/devnotes/cabinet-api-functions)。

根據信任和瀏覽器安全性層級設定，可能會顯示認證來識別簽章的個人或公司。 如果安全性層級是 [無]，或帶正負號的控制憑證擁有者是受信任，不會顯示憑證。 請參閱[Internet Explorer 瀏覽器安全性層級和控制項行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)如需有關如何瀏覽器安全性設定會決定您的控制項是否會下載和顯示的憑證。

數位簽署可保證程式碼尚未變更，因為它尚未簽署。 程式碼的雜湊是採取，而且內嵌在憑證中。 此雜湊稍後會與下載的程式碼之後，但會在執行之前所採取的程式碼的雜湊進行比較。 Verisign 等公司可以提供簽署的程式碼所需的私人和公用金鑰。 ActiveX SDK 隨附 MakeCert 來建立測試憑證的公用程式。

##  <a name="_core_managing_the_palette"></a> 管理調色盤

容器判斷調色盤，並使其可為環境屬性， **DISPID_AMBIENT_PALETTE**。 (例如，Internet Explorer) 的容器選擇調色盤頁面上的所有 ActiveX 控制項用來判斷他們自己的調色盤。 這可防止顯示閃爍，並提供一致的外觀。

控制項可以覆寫`OnAmbientPropertyChange`來處理變更調色盤的通知。

控制項可以覆寫`OnGetColorSet`傳回設為繪製調色盤的色彩。 容器會使用傳回的值，判斷控制項是否調色盤感知。

在 OCX 96 指導方針中，控制項必須一律會了解其在背景中的調色盤。

不要使用環境的調色盤屬性的舊容器會傳送 WM_QUERYNEWPALETTE 和 WM_PALETTECHANGED 的訊息。 控制項可以覆寫`OnQueryNewPalette`和`OnPaletteChanged`來處理這些訊息。

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Internet Explorer 瀏覽器安全性層級和控制行為

在瀏覽器具有安全性層級，可由使用者設定的選項。 由於網頁可包含主動式內容可能會傷害使用者的電腦，瀏覽器就會允許使用者選取的安全性層級的選項。 視瀏覽器實作的安全性層級的方式，而定，可能不會下載或將會顯示憑證或警告訊息，以便允許使用者選擇在執行階段要下載此控制項的控制項。 高、 中和低安全性等級下在 Internet Explorer 的 ActiveX 控制項的行為如下所示。

### <a name="high-safety-mode"></a>高安全性模式

- 不帶正負號的控制項將不會被下載。

- 如果未受信任的已簽署的控制項將顯示憑證 （使用者可以選擇的選項，以永遠信任這個憑證擁有者的程式碼從現在起）。

- 標示為安全的控制項將會有持續性資料及/或可編寫指令碼。

### <a name="medium-safety-mode"></a>中的安全性模式

- 不帶正負號的控制項將會顯示在下載之前的警告。

- 帶正負號的控制項將顯示未受信任的憑證。

- 未標示為安全的控制項將會顯示警告。

### <a name="low-safety-mode"></a>低安全性模式

- 下載控制項時，而不發出警告。

- 發生指令碼處理和持續性，而不發出警告。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC ActiveX 控制項：授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

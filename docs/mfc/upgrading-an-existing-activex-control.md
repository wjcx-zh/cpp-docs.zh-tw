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
ms.openlocfilehash: dfee42369b698956f4f91ab61a1f37e0ef06d9f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754512"
---
# <a name="upgrading-an-existing-activex-control"></a>升級現有的 ActiveX 控制項

現有的 ActiveX 控件(以前的 OLE 控制件)無需修改即可在 Internet 上使用。 但是,您可能希望修改控件以提高其性能。

> [!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

在 Web 頁上使用控制件時,還有其他注意事項。 .ocx 檔和所有支援文件必須在目標計算機上或通過互聯網下載。 這使得代碼大小和下載時間成為一個重要的考慮因素。 下載可以打包在簽名的 .cab 檔中。 您可以將控制項標記為腳本化安全,並且標記為安全初始化。

本文章討論下列主題：

- [下載的包裝碼](#_core_packaging_code_for_downloading)

- [為文稿化與初始化標記控制安全](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [授權問題](#_core_licensing_issues)

- [簽署代碼](#_core_signing_code)

- [管理調色盤](#_core_managing_the_palette)

- [網際網路瀏覽器瀏覽器安全等級和控制行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

您還可以添加優化,如[ActiveX 控件:優化](../mfc/mfc-activex-controls-optimization.md)中所述。 例如,在[Internet 上的 ActiveX 控制件](../mfc/activex-controls-on-the-internet.md)中所述,Monikers 可用於非同步下載屬性和大型 BLOB。

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a>下載的包裝碼

有關此主題的詳細資訊,請參閱打包[ActiveX 控制件](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29)。

### <a name="the-codebase-tag"></a>CODEBASE 標籤

ActiveX 控制項使用標記嵌入到網頁`<OBJECT>`中 。 標記`CODEBASE``<OBJECT>`的 參數指定從中下載控制項的位置。 `CODEBASE`可以成功指向許多不同的文件類型。

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>將 CODEBASE 標籤與 OCX 檔一起使用

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

此解決方案僅下載控制項的.ocx檔,並要求已在用戶端電腦上安裝任何支援 DLL。 這將適用於使用視覺C++構建的 Internet Explorer 和 MFC ActiveX 控件,因為 Internet Explorer 附帶支援用於視覺C++控件的 LLL。 如果使用另一個支援 ActiveX 控制的 Internet 瀏覽器查看此控制項,則此解決方案將不起作用。

### <a name="using-the-codebase-tag-with-an-inf-file"></a>將 CODEBASE 標籤與 INF 檔案一起使用

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

.inf 檔將控制 .ocx 及其支援檔的安裝。 不建議使用此方法,因為無法對 .inf 文件進行簽名(請參閱代碼簽名指標[的簽名代碼](#_core_signing_code))。

### <a name="using-the-codebase-tag-with-a-cab-file"></a>將 CODEBASE 標籤與 CAB 檔案一起使用

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

機櫃檔是打包使用 MFC 的 ActiveX 控件的推薦方法。 在檔案櫃檔中打包 MFC ActiveX 控制件允許包含 .inf 檔案來控制 ActiveX 控制件和任何從屬 DLL(如 MFC DLL)的安裝。 使用 CAB 檔會自動壓縮代碼,以便更快地下載。 如果使用 .cab 檔進行元件下載,則對整個 .cab 檔進行簽名比每個單獨的元件更快。

### <a name="creating-cab-files"></a>建立 CAB 檔案

創建檔案櫃檔的工具現在是[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)的一部分。

指向的`CODEBASE`機櫃檔應包含 ActiveX 控制件的 .ocx 檔和用於控制其安裝的 .inf 檔。 通過指定控制檔和 .inf 檔案的名稱來創建檔案櫃檔。 請勿包括此檔櫃檔中系統中可能已經存在的從屬 DLL。 例如,MFC DLL 打包在單獨的檔櫃檔中,並由控制 .inf 檔案引用。

有關如何建立 CAB 檔的詳細資訊,請參考[BAB 檔案](/windows/win32/devnotes/cabinet-api-functions)。

### <a name="the-inf-file"></a>INF 檔案

下面的範例 spindial.inf 列出了支援檔和 MFC 自旋控制所需的版本資訊。 請注意,MFC DLL 的位置是 Microsoft 網站。 mfc42.cab 由微軟提供並簽名。

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

### <a name="the-object-tag"></a>物件\<>标记

下面的範例演示了`<OBJECT>`使用標記打包 MFC 旋轉採樣控制件。

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

在這種情況下,spindial.cab 將包含兩個檔,自旋.ocx 和 spindial.inf。 以下指令將產生檔案櫃檔:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

參數`-s 6144`在機櫃中保留用於代碼簽名的空間。

### <a name="the-version-tag"></a>版本標記

請注意,`#Version`使用 CAB 檔`<OBJECT>`指定的資訊適用於 標記的*CLASSID*參數指定的控制項。

根據指定的版本,您可以強制下載控制項。 有關標記的完整規格(`OBJECT`包括*CODEBASE*參數),請參閱 W3C 參考。

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>為文稿化與初始化標記控制安全

在網頁中使用的 ActiveX 控件應標記為腳本安全,如果實際上是安全的,則對於初始化是安全的。 安全控制不會直接執行磁碟 IO 或存取電腦的記憶體或寄存器。

控件可以標記為腳本安全,並且對於通過註冊表進行初始化是安全的。 修改`DllRegisterServer`以添加類似於以下內容的條目,以將控制項標記為註冊表中的腳本和持久性安全。 另一種方法是實現`IObjectSafety`。

您將為控制項定義 GUID(全域唯一識別子),以將其標記為腳本和持久性安全。 可以安全編寫文稿的控制項將包含類似於以下內容的註冊表項:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

可以從持久資料安全地初始化的控制項標記為安全的持久性,註冊表項類似於:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

新增類似於以下內容的項目(取代控制項的類別代碼 )`{06889605-B8D0-101A-91F1-00608CEAD5B3}`以將金鑰與以下類別 ID 相關聯:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a>許可問題

如果要在 Web 頁上使用許可控制項,則必須驗證許可協定是否允許在 Internet 上使用該控制項,並為其創建許可證套件檔 (LPK)。

如果運行 Internet Explorer 的電腦未獲得使用該控制件的許可,則許可的 ActiveX 控制件將無法正確載入 HTML 頁中。 例如,如果使用 Visual C++構建許可控制項,則使用該控制項的 HTML 頁將正確載入到生成控制項的電腦上,但除非包含許可資訊,否則該控制檔不會載入到其他電腦上。

要在網際網路資源管理員使用授權的 ActiveX 控制項,必須檢查供應商的授權協定,以驗證控制項的授權是否允許:

- 可轉散發

- 網際網路控制的使用

- 使用程式庫參數

要在非授權電腦上的 HTML 頁中使用許可控制項,必須生成許可證套件檔 (LPK)。 LPK 檔包含 HTML 頁中許可控制件的執行時許可證。 此文件通過LPK_TOOL生成。ActiveX SDK 附帶的 EXE。

#### <a name="to-create-an-lpk-file"></a>建立 LPK 檔案

1. 運行LPK_TOOL。授權使用該控制件的電腦上的 EXE。

1. 在 **「許可證套件創作工具」** 對話方塊中,在 **「可用控制件」** 清單框中,選擇將在 HTML 頁面上使用的每個許可的 ActiveX 控制件,然後按下「**添加**」。

1. 按下 **「保存&退出**併鍵入 LPK 檔的名稱。 這將創建 LPK 檔並關閉應用程式。

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>嵌入 HTML 頁面內嵌入授權的元件

1. 編輯 HTML 頁面。 在 HTML 頁\<中,\<在任何其他 OBJECT> 標記之前插入許可證管理器物件的 OBJECT>标记。 許可證管理員是一個 ActiveX 控制項,隨 Internet 資源管理器一起安裝。 其類 ID 如下所示。 將授權管理員物件的 LPKPath 屬性設置為 LPK 檔的路徑和名稱。 每個 HTML 頁只能有一個 LPK 檔。

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. 在\<許可證管理器標記後插入許可控制項的物件>標記。

   例如,顯示 Microsoft 遮罩編輯控制件的 HTML 頁面如下所示。 第一類 ID 用於許可證管理器控制項,第二類 ID 用於「遮罩編輯」控制件。 更改標記以指向之前創建的 .lpk 檔的相對路徑,並添加物件標記,包括控制項的類 ID。

1. 如果使用\<NCompass ActiveX 外掛程式,請插入 LPK 檔的 EMBED>属性。

   如果可以在其他啟用"活動"的瀏覽器上查看您的控制項(例如,使用 NCompass ActiveX 外掛程式的 Netscape),\<則必須添加 EMBED>语法,如下所示。

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

有關控制項授權的詳細資訊,請參閱[ActiveX 控制件:授權 ActiveX 控制件](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

## <a name="signing-code"></a><a name="_core_signing_code"></a>簽署代碼

代碼簽名旨在標識代碼源,並保證代碼自簽名以來未發生更改。 根據瀏覽器安全設置,在下載代碼之前可能會警告使用者。 用戶可以選擇信任某些證書擁有者或公司,在這種情況下,由受信任者簽名的代碼將在沒有警告的情況下下載。 代碼通過數字簽名,以避免篡改。

請確保您的最終代碼已簽名,以便可以自動下載控制項,而無需顯示信任警告消息。 有關如何對程式碼進行簽署的詳細資訊,請查看 ActiveX SDK 中的身份驗證文件,請參閱簽署[CAB 檔](/windows/win32/devnotes/cabinet-api-functions)。

根據信任和瀏覽器安全級別設置,可能會顯示證書以標識簽名人或公司。 如果安全級別為 none,或者簽名控制件的證書擁有者受信任,將不會顯示證書。 有關如何下載控制項和顯示憑證的詳細資訊,請參閱[Internet Explorer 瀏覽器瀏覽器安全等級和控制行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)。

數位簽名保證代碼自簽名以來未更改。 獲取代碼的哈希並嵌入到證書中。 稍後,此哈希與下載代碼後但在運行之前獲取的代碼的哈希進行比較。 威瑞信等公司可以提供簽名代碼所需的私鑰和公開金鑰。 ActiveX SDK 附帶 MakeCert,這是一個用於創建測試證書的實用程式。

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a>管理調色盤

容器確定調色板,並將其作為環境屬性提供 **,DISPID_AMBIENT_PALETTE**。 容器(例如,Internet Explorer)選擇頁面上所有 ActiveX 控制項使用的調色板來確定自己的調色板。 這樣可以防止顯示閃爍,並呈現一致的外觀。

控制項可以重寫`OnAmbientPropertyChange`以處理對調色板的更改通知。

控制項可以重寫`OnGetColorSet`以返回顏色集以繪製調色板。 容器使用返回值來確定控制項是否具有調色板感知性。

根據 OCX 96 準則,控件必須始終在後台實現其調色板。

不使用環境調色板屬性的舊容器將發送WM_QUERYNEWPALETTE和WM_PALETTECHANGED消息。 控件可以重寫`OnQueryNewPalette`和處理`OnPaletteChanged`這些消息。

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>網際網路瀏覽器瀏覽器安全等級和控制行為

瀏覽器具有安全級別選項,由使用者配置。 由於網頁可能包含可能損害使用者計算機的活動內容,因此瀏覽器允許使用者選擇安全級別選項。 根據瀏覽器實現安全級別的方式,控件可能根本不下載,或者將顯示證書或警告消息,以允許使用者在運行時選擇是否下載控件。 下面列出了 Internet Explorer 上高、中、低安全級別下 ActiveX 控件的行為。

### <a name="high-safety-mode"></a>高安全模式

- 將不會下載未簽名的控制項。

- 如果不受信任,簽名的控制項將顯示證書(用戶可以選擇一個選項,以便從現在起始終信任來自此證書擁有者的代碼)。

- 只有標記為安全的控制項才會具有持久性資料和/或可編寫腳本。

### <a name="medium-safety-mode"></a>中型安全模式

- 未簽名的控制器將在下載前顯示警告。

- 如果不受信任,簽名的控制項將顯示證書。

- 未標記為安全的控制項將顯示警告。

### <a name="low-safety-mode"></a>低安全模式

- 在未發出警告的情況下下載控制項。

- 腳本和持久性在沒有任何警告的情況下進行。

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC ActiveX 控制項：授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

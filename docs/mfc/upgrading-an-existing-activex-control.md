---
title: "升級現有的 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 網際網路"
  - "CAB 檔案, ActiveX 控制項"
  - "網際網路應用程式 [C++], ActiveX 控制項"
  - "網際網路應用程式 [C++], 封裝程式碼進行下載"
  - "授權 ActiveX 控制項"
  - "網際網路控制項的 LPK 檔案"
  - "OLE 控制項 [C++], 升級至 ActiveX"
  - "可安全用於指令碼編寫和初始化 (控制項)"
  - "升級 ActiveX 控制項"
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 升級現有的 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

現有的 ActiveX 控制項 \(先前稱為 OLE automation 控制項\) 在網際網路上使用，而不需要修改。  不過，您可以修改控制項改善其效能。  當您在 Web 網頁中的控制項，有一些額外的考量。  必須在目標電腦上或跨網際網路下載 .ocx 檔和所有支援的檔案。  這個程式碼大小和下載時間重要考量。  下載在已簽署的 .cab 檔案可以封裝。  您可以將您的控制項相同安全做為指令碼，並以初始化的安全。  
  
 本文章將討論下列主題：  
  
-   [封裝程式碼進行下載](#_core_packaging_code_for_downloading)  
  
-   [標記指令碼和初始化的安全控制項](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
-   [允許發行](#_core_licensing_issues)  
  
-   [程式碼簽章](#_core_signing_code)  
  
-   [處理調色盤](#_core_managing_the_palette)  
  
-   [Internet Explorer 瀏覽器安全性層級和控制項的行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 您也可以將最佳化，如 [ActiveX 控制項:最佳化](../mfc/mfc-activex-controls-optimization.md)中所述。  標記可用來下載屬性和大 Blob 非同步，如 [在網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)中所述。  
  
##  <a name="_core_packaging_code_for_downloading"></a> 封裝程式碼進行下載  
 如需這方面的詳細資訊，請參閱知識庫文件包裝的 MFC 控制項為使用對網際網路」\(Q167158\)。  您可以在 MSDN Library CD\-ROM 或是在 [http:\/\/support.microsoft.com\/support](http://support.microsoft.com/support) 找到知識庫文件。  
  
### CODEBASE 標記  
 使用 `<OBJECT>` 標記， ActiveX 控制項在 Web 網頁中。  `<OBJECT>` 標記為 `CODEBASE` 參數指定下載控制項的位置。  `CODEBASE` 可以成功點在許多不同的檔案類型。  
  
### 使用與 OCX 檔案的 CODEBASE 標記  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,70,0,1086"  
```  
  
 這個方案在用戶端機器下載只有控制項的 .ocx 檔案，但需要所有支援的 DLL 已經安裝。  因為 Internet Explorer 隨附於 Visual C\+\+ 的控制項，支援的 DLL 對於以 Visual C\+\+ 和 MFC ActiveX 控制項將建置的 Internet Explorer。  如果是控制項功能的 ActiveX 的其他網際網路瀏覽器來檢視這個控制項，此方案就無法運作。  
  
### 使用與 INF 檔案的 CODEBASE 標記  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 .inf 檔案會控制 .ocx 及其支援的檔案的安裝。  不建議使用這個方法，因為是不可能的簽署 .inf 檔 \(在程式碼的指標 \(請參閱 [簽署的程式碼](#_core_signing_code) \)。  
  
### 使用與 CAB 檔案的 CODEBASE 標記  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,2,0,0"  
```  
  
 封包檔是這個建議的方式包裝 ActiveX 控制項使用配置 MFC。  包裝在封包檔的 MFC ActiveX 控制項允許 .inf 檔案包含控制項的 ActiveX 控制項和任何相依 DLL 的安裝 \(例如 MFC DLL\)。  使用封包檔封包檔自動壓縮加快下載的程式碼。  如果您為元件下載使用 .cab 檔案，它比個別元件是快速簽署整份 .cab 檔案。  
  
### 建立 CAB 檔案  
 您可以從知識庫文件的 [310618:Microsoft 封包軟體開發套件 \(SDK\)。](http://go.microsoft.com/fwlink/?LinkId=148204)封包開發套件。  在這個套件您會發現有必要的工具建構封包檔。  
  
 封包檔指向 `CODEBASE` 應包含您的 ActiveX 控制項的 .ocx 檔和 .inf 檔控制其安裝。  您可以指定控制項檔和 .inf 檔案名稱建立封包檔。  不要包含在這個封包檔的系統可能已經存在的相依 DLL。  例如， MFC DLL 安裝在不同的封包檔封裝並由控制 .inf 檔案參考。  
  
 如需的詳細資料建立封包檔封包檔，請參閱 [建立封包檔封包檔](http://msdn.microsoft.com/zh-tw/cc52fd09-bdf6-4410-a693-149a308f36a3)。  
  
### INF 檔：  
 下列範例中 spindial.inf、清單支援的檔案和版本資訊 Spindial MFC 控制項需要。  請注意 MFC 的 DLL 位置是 Microsoft 網站。  Microsoft 提供這個 mfc42.cab 和簽署。  
  
```  
Contents of spindial.inf:  
[mfc42installer]   
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab   
[Olepro32.dll] - FileVersion=5,0,4261,0  
[Mfc42.dll] - FileVersion=6,0,8168,0  
[Msvcrt.dll] - FileVersion=6,0,8168,0  
```  
  
### \<OBJECT\> 標記  
 以下範例說明 `<OBJECT>` 標記換行 MFC Spindial 範例控制項。  
  
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
  
 在這種情況下， spindial.cab 將包含兩個檔案， spindial.ocx 和 spindial.inf。  下列命令會建立封包檔:  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 `–s 6144` 參數為程式碼簽署保留在封包的空間。  
  
### 版本標記  
 請注意此 `#Version` 資訊與指定封包檔封包檔適用於 `<OBJECT>` 標記為 `CLASSID` 參數指定的控制項。  
  
 根據指定的版本，強制控制項下載。  如需 `OBJECT` 標記的完整規格中 `CODEBASE` 參數，請參閱 W3C 參考。  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> 標記指令碼和初始化的安全控制項  
 如果它們實際上是安全的，應該將用於 Web 網頁的 ActiveX 控制項做為指令碼的初始化的安全和安全。  安全控制項不會執行磁碟 IO 也不會直接存取電腦的記憶體或暫存器。  
  
 控制項可以標記為的指令碼初始化的安全和安全向註冊。  修改 `DllRegisterServer` 將輸入類似下列標記控制項做為指令碼並繼續的安全在登錄中。  另一個將會實作 `IObjectSafety`。  
  
 您要定義 GUID \(全域唯一識別項\) 的控制項可以標記為安全做為指令碼和持續性的。  可以安全地指令碼的控制項會包含登錄項目如下所示:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 可以從持續性資料安全地初始化的控制項是持續性的標記為安全與登錄項目類似:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 加入項目類似 \(替代控制項的類別 ID 在 `{06889605-B8D0-101A-91F1-00608CEAD5B3}`位置\) 使索引鍵的下列與下列類別 ID:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> 允許發行  
 如果您要在 Web 網頁上使用授權控制項，您必須確認授權合約可讓它在網際網路上使用和建立授權封裝檔案 \(LPK\) 其。  
  
 如果執行 Internet Explorer 的電腦未授權控制項，授權的 ActiveX 控制項在 HTML 網頁無法正確地載入。  例如，如果使用，則 Visual C\+\+，授權控制項已經建立，使用控制項的 HTML 網頁在控制項中建立的電腦將會正確載入，不過，它在不同的電腦上不會載入，除非授權資訊是包含的。  
  
 若要使用授權的 ActiveX 控制項在 Internet Explorer 中，您必須檢查廠商的授權合約驗證控制項的授權授與使用權限:  
  
-   轉散發  
  
-   在網際網路上的控制項  
  
-   對 Codebase 參數的用途  
  
 若要使用授權控制項在 nonlicensed 電腦的 HTML 網頁，您必須產生授權封裝檔案 \(LPK\)。  LPK 檔案在 HTML 網頁包含授權控制項的執行階段授權。  這個檔案會隨附 ActiveX SDK 的 LPK\_TOOL.EXE 產生。  如需詳細資訊，請參閱 MSDN 網站：[http:\/\/msdn.microsoft.com](http://msdn.microsoft.com)。  
  
#### 若要建立 LPK 檔  
  
1.  在授權使用控制項的電腦上 LPK\_TOOL.EXE。  
  
2.  在 **License Package Authoring Tool** 對話方塊，在 **Available Controls** 清單方塊中，選取 HTML 網頁並按一下 **Add**所使用的每個授權的 ActiveX 控制項。  
  
3.  按一下 **Save & Exit** 並為 LPK 檔案輸入名稱。  這會建立 LPK 檔案並結束應用程式。  
  
#### 內嵌在 HTML 網頁的授權控制項。  
  
1.  編輯您的 HTML 網頁。  在 HTML 網頁，請在任何其他 \<OBJECT\> 標記之前插入授權管理員物件 \<OBJECT\> 標記。  安裝與 Internet Explorer 的授權管理員是 ActiveX 控制項。  它的類別 ID 如下所示。  設定授權管理員物件的 LPKPath 屬性設定為 LPK 檔案的路徑和名稱。  每個 HTML 網頁只能有一個 LPK 檔案。  
  
    ```  
    <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
        <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
    </OBJECT>  
    ```  
  
2.  插入 \<OBJECT\> 標記於您的授權控制項，在授權管理員標記之後。  
  
     例如，顯示 Microsoft 格式編輯控制項的 HTML 網頁如下所示。  第一個 ID 代表授權管理員控制項， ID 是格式編輯控制項的第二個類別。  將標記加入至您先前建立 .lpk 檔案的相對路徑的點，並將物件標記包含控制項的類別 ID。  
  
3.  插入您的 \<LPK 檔案的內嵌\> 屬性，則為，如果使用 NCompass ActiveX 插入。  
  
     如果控制項在其他使用中允許瀏覽器中檢視 \(例如，使用 NCompass ActiveX 插入 Netscape —您必須將內嵌 \<\> 語法如下所示。  
  
    ```  
    <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
        <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
  
        <EMBED SRC = "maskedit.LPK">  
  
    </OBJECT>  
    <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
    </OBJECT>  
    ```  
  
 如需您所建立的控制項授權的詳細資訊，請參閱[授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
##  <a name="_core_signing_code"></a> 程式碼簽章  
 程式碼簽署是設計來識別程式碼來源並確保程式碼未變更，因為它簽署。  根據瀏覽器安全性設定，因此，在程式碼下載之前，使用者可能會對您發出警告。  使用者可以選擇部分信任憑證持有者或公司，在這種情況下，這些簽署程式碼受信任要下載的情況下，在沒有產生警告。  程式碼數位簽署避免竄改。  
  
 判斷您最後的程式碼簽署，讓控制項可以自動下載，而不顯示信任警告訊息。  如需的詳細資料簽署程式碼，請檢查 Authenticode 簽章的文件在 ActiveX SDK 並參閱 [簽署封包檔封包檔](http://msdn.microsoft.com/zh-tw/04d8b47a-8f1c-4b54-ab90-730fcdc03747)。  
  
 根據信任和瀏覽器安全性層級設定，憑證可以顯示識別這個簽章的人員或公司。  如果安全性層級是 None，則為，如果符號控制的憑證持有者信任憑證，不會顯示。  請參閱 [Internet Explorer 瀏覽器安全性層級和控制項的行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior) 。如需詳細的瀏覽器安全性設定來決定控制項是否下載，以及該憑證隨即顯示。  
  
 因為它已簽署，數位簽章確保程式碼未變更。  程式碼的雜湊在憑證中取得並內嵌。  這個雜湊之後比較拍攝之程式碼的雜湊，在程式碼下載後，但是，在執行之前。  例如公司 Verisign 能提供必要的私用和公用金鑰簽署程式碼。  ActiveX SDK 隨附 MakeCert，建立的測試憑證公用程式。  
  
##  <a name="_core_managing_the_palette"></a> 處理調色盤  
 容器判斷調色盤並使其可以為環境屬性， **DISPID\_AMBIENT\_PALETTE**。  容器 \(例如， Internet Explorer\) 所選取頁面上的所有 ActiveX 控制項可以決定自己的調色盤的調色盤。  這可防止顯示閃動問題並提供一致的外觀。  
  
 控制項可以覆寫由 `OnAmbientPropertyChange` 管理的變更通知的調色盤。  
  
 控制項可以覆寫由 `OnGetColorSet` 傳回色彩設定繪製調色盤。  容器使用傳回值判斷控制項是否為調色盤感知。  
  
 根據 OCX 96 方針，控制項必須永遠是實現其在背景的調色盤。  
  
 不使用環境調色盤屬性的較舊的容器中傳送 `WM_QUERYNEWPALETTE` 和 `WM_PALETTECHANGED` 資訊。  控制項可以覆寫由 `OnQueryNewPalette` 和 `OnPaletteChanged` 處理這些訊息。  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Internet Explorer 瀏覽器安全性層級和控制項的行為  
 瀏覽器有安全性層級的選項，可由使用者。  由於網頁可能包含可能會危及使用者電腦的主動式內容，瀏覽器允許使用者指定安全性層級的選項。  根據這個模式瀏覽器實作安全性層級，控制項不可以下載，也不會顯示憑證或一個警告訊息允許使用者在執行階段選取下載控制項。  ActiveX 控制項行為在高、中或低安全性層級下的 Internet Explorer 列示如下。  
  
### 高安全性模式。  
  
-   不帶正負號的控制項不會下載。  
  
-   符號控制項會顯示憑證，如果不信任 \(使用者可以選取從現在開始永遠信任這憑證持有者的程式碼\)。  
  
-   成安全標記的控制項只會有持續性資料和 \(或\) 可編寫指令碼。  
  
### 媒體安全性模式。  
  
-   不帶正負號的控制項在下載前會顯示警告。  
  
-   符號控制項會顯示憑證，如果不信任。  
  
-   成安全未標記的控制項會顯示警告。  
  
### 低安全性模式。  
  
-   控制下載，而不需警告。  
  
-   指令碼並繼續執行，而不需警告。  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [MFC ActiveX 控制項：授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
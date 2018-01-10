---
title: "升級現有的 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a7b9c76ffd4366522dce366a165698bd3a26173
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="upgrading-an-existing-activex-control"></a>升級現有的 ActiveX 控制項
現有的 ActiveX 控制項 （先前稱為 OLE 控制項） 可用不經修改網際網路上。 不過，您可以修改控制項以改善其效能。 當使用您在網頁上的控制項，還有其他考量。 .Ocx 檔案與所有支援的檔案必須是目標電腦上，或透過網際網路下載。 這可讓程式碼大小和下載時間的重要考量。 下載可封裝在簽署的.cab 檔案。 您可以標示為安全用於指令碼，以及用於初始化安全控制項。  
  
 本文將討論下列主題：  
  
- [封裝程式碼進行下載](#_core_packaging_code_for_downloading)  
  
- [在指令碼和初始化標記控制項安全](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
- [授權問題](#_core_licensing_issues)  
  
- [程式碼簽章](#_core_signing_code)  
  
- [管理調色盤](#_core_managing_the_palette)  
  
- [Internet Explorer 瀏覽器安全性層級和控制行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 您也可以如所述新增最佳化， [ActiveX 控制項： 最佳化](../mfc/mfc-activex-controls-optimization.md)。 Moniker 可以用來下載屬性和大型 Blob 以非同步方式中所述[網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)。  
  
##  <a name="_core_packaging_code_for_downloading"></a>封裝程式碼進行下載  
 如需有關這個主題的詳細資訊，請參閱知識庫文章 「 封裝 MFC 控制項的使用透過網際網路 」 (Q167158)。 您可以找到知識庫文件在[http://support.microsoft.com/support](http://support.microsoft.com/support)。  
  
### <a name="the-codebase-tag"></a>程式碼基底標記  
 ActiveX 控制項內嵌在網頁使用`<OBJECT>`標記。 `CODEBASE`參數`<OBJECT>`標記用來指定要從中下載此控制項的位置。 `CODEBASE`可以指向不同的檔案類型的數目已成功。  
  
### <a name="using-the-codebase-tag-with-an-ocx-file"></a>使用程式碼基底標記與 OCX 檔案  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"  
```  
  
 下載只控制項的.ocx 檔案，此解決方案，並會要求用戶端電腦上已經安裝任何支援 Dll。 這適用於 Internet Explorer 和 MFC ActiveX 控制項建置 Visual c + + 中，因為 Internet Explorer 隨附的 Visual c + + 控制項支援的 Dll。 如果是 ActiveX 控制項支援的其他網際網路瀏覽器來檢視此控制項，此方案將無法運作。  
  
### <a name="using-the-codebase-tag-with-an-inf-file"></a>INF 檔案搭配使用的程式碼基底標記  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 .inf 檔案就會控制安裝.ocx 和其支援的檔案。 因為無法簽署.inf 檔案，不建議這個方法 (請參閱[簽署程式碼](#_core_signing_code)指標在程式碼簽署)。  
  
### <a name="using-the-codebase-tag-with-a-cab-file"></a>使用程式碼基底標記的封包檔  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"  
```  
  
 封包檔的建議方式是使用 MFC 的封裝 ActiveX 控制項。 封裝的封包檔中的 MFC ActiveX 控制項可讓.inf 檔案，包含要安裝的 ActiveX 控制項和任何相依的 Dll （例如 MFC Dll) 的控制項。 使用的封包檔自動壓縮速度較快的下載程式碼。 如果您將元件下載的.cab 檔，則速度來簽署整個.cab 檔案比個別元件。  
  
### <a name="creating-cab-files"></a>建立 CAB 檔案  
 您可以從知識庫文件下載封包開發套件[310618: Microsoft 封包軟體開發套件](http://go.microsoft.com/fwlink/p/?linkid=148204)。 在此套件中，您會找到必要的工具，來建構封包檔。  
  
 所指向的封包檔`CODEBASE`應該包含您的 ActiveX 控制項的.ocx 檔案和.inf 檔來控制其安裝。 您建立的封包檔，藉由指定控制項檔案的名稱和.inf 檔案。 不包含此封包檔中的系統可能已存在的相依 Dll。 例如，MFC Dll 封裝在個別的封包檔，而且所控制的.inf 檔案參考。  
  
 如需有關如何建立封包檔的詳細資訊，請參閱[建立封包檔](http://msdn.microsoft.com/en-us/cc52fd09-bdf6-4410-a693-149a308f36a3)。  
  
### <a name="the-inf-file"></a>INF 檔案  
 下列範例、 spindial.inf、 清單支援的檔案和版本資訊所需的 MFC Spindial 控制。 請注意 MFC Dll 的位置是 Microsoft 的網站。 Mfc42.cab 上提供及經過 Microsoft 簽署。  
  
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
  
 在此情況下，spindial.cab 會包含兩個檔案、 spindial.ocx 和 spindial.inf。 下列命令會建立封包檔：  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 `-s 6144`參數保留在程式碼簽署封包中的空間。  
  
### <a name="the-version-tag"></a>版本標記  
 請注意這裡`#Version`指定封包檔的資訊適用於所指定的控制項`CLASSID`參數`<OBJECT>`標記。  
  
 根據指定的版本，您可以強制下載您的控制項。 完整規格`OBJECT`標記包括`CODEBASE`參數，請參閱 W3C 參考。  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>在指令碼和初始化標記控制項安全  
 在網頁中使用的 ActiveX 控制項應該標示為安全用於指令碼和初始化如果實際上是安全。 安全控制項不會執行磁碟 IO，或直接存取的記憶體或電腦的暫存器。  
  
 控制項可以標示為安全用於指令碼和初始化透過登錄中。 修改`DllRegisterServer`新增項目與以下類似標記為安全的指令碼和登錄中的持續性的控制項。 替代方法是實作`IObjectSafety`。  
  
 您會定義 Guid （全域唯一識別項） 來標示指令碼和持續性的安全控制項。 可以安全地編寫指令碼的控制項將會包含類似下列的登錄項目：  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 從持續性資料能夠安全地初始化的控制項是標示為安全的持續性與登錄項目類似的：  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 加入與下列類似的項目 (替代控制項的類別識別碼取代`{06889605-B8D0-101A-91F1-00608CEAD5B3}`) 您的金鑰與下列類別識別碼：  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a>授權問題  
 如果您想要使用授權的控制項在網頁上，您必須確認授權合約可讓網際網路上的使用，並為其建立的授權封裝檔案 (LPK)。  
  
 授權的 ActiveX 控制項將不會載入正確的 HTML 網頁中如果執行 Internet Explorer 的電腦未獲授權使用的控制項。 例如，如果使用 Visual c + + 建置授權的控制項時，使用控制項的 HTML 網頁將會正確載入其中建立此控制項，但它將不會載入在不同電腦上未包含授權資訊，除非在電腦上。  
  
 若要在 Internet Explorer 中使用授權的 ActiveX 控制項，您必須檢查廠商的授權合約，以確認控制項授權的允許：  
  
-   轉散發  
  
-   使用在網際網路上控制  
  
-   使用程式碼基底參數  
  
 若要在 HTML 網頁要在未經授權的電腦上使用授權的控制項，您必須產生的授權封裝檔案 (LPK)。 LPK 檔案包含授權控制項的 HTML 網頁上的執行階段授權。 這個檔案是透過 LPK_TOOL 產生。ActiveX SDK 隨附的 EXE。 如需詳細資訊，請參閱 MSDN 網站，網址[http://msdn.microsoft.com](http://msdn.microsoft.com)。  
  
#### <a name="to-create-an-lpk-file"></a>若要建立的 LPK 檔案  
  
1.  執行 LPK_TOOL。已授權可使用控制項的電腦上的 EXE。  
  
2.  在**授權封裝 Authoring Tool**對話方塊中，於**可用控制項**清單方塊中，選取每個授權的 ActiveX 控制項，它會使用 HTML 頁面上，按一下 **新增**.  
  
3.  按一下**儲存並結束**輸入 LPK 檔案的名稱。 這會建立 LPK 檔案並關閉應用程式。  
  
#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>若要內嵌在 HTML 網頁上授權的控制項  
  
1.  編輯 HTML 網頁。 在 HTML 頁面中，插入\<物件 > 標記之前的任何其他授權管理員物件\<物件 > 標記。 授權管理員是已安裝 Internet Explorer 使用 ActiveX 控制項。 它的類別 ID 如下所示。 授權管理員物件的 LPKPath 屬性設 LPK 檔案的名稱與路徑。 您可以有只有一個 LPK 檔案，每個 HTML 網頁。  
  
 ```  
 <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
 </OBJECT>  
 ```  
  
2.  插入\<物件 > 授權管理員標記之後授權控制項的標記。  
  
     例如，如下所示顯示 Microsoft 遮罩編輯控制項的 HTML 網頁。 識別碼是授權管理員控制的第一個類別，第二個類別識別碼是遮罩編輯控制項。 變更為指向您先前建立的.lpk 檔案的相對路徑的標記，並加入控制項的類別 id 的物件標記。  
  
3.  插入\<內嵌 > LPK 檔案屬性，如果使用 NCompass ActiveX 外掛程式。  
  
     如果您的控制項可以檢視上其他作用中啟用瀏覽器 — 比方說，使用 NCompass ActiveX 外掛程式 Netscape — 您必須新增\<內嵌 > 語法如下所示。  
  
 ```  
 <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
 
 <EMBED SRC = "maskedit.LPK">  
 
 </OBJECT>  
 <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
 </OBJECT>  
 ```  
  
 如需控制項授權的詳細資訊，請參閱[ActiveX 控制項： 授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
##  <a name="_core_signing_code"></a>程式碼簽章  
 程式碼簽章設計來識別程式碼中，來源，以及簽署以確保程式碼，因為它並未變更。 根據瀏覽器安全性設定之前下載的程式碼, 可能會警告使用者。 使用者可以選擇要信任特定憑證擁有者或公司，在其中案例的程式碼簽署的那些信任會被下載，而不發出警告。 程式碼是數位簽章以避免遭到竄改。  
  
 請確定您最後的程式碼簽署，讓您控制自動下載但不顯示信任警告訊息。 如需有關如何簽署程式碼的詳細資訊，請檢查 Authenticode ActiveX SDK 中提供的文件，並查看[簽章的封包檔](http://msdn.microsoft.com/en-us/04d8b47a-8f1c-4b54-ab90-730fcdc03747)。  
  
 根據信任和瀏覽器的安全性層級設定，可能顯示憑證識別簽署的個人或公司。 如果安全性層級為 none，或帶正負號的控制憑證擁有者是受信任，不會顯示憑證。 請參閱[Internet Explorer 瀏覽器安全性層級和控制行為](#_core_internet_explorer_browser_safety_levels_and_control_behavior)如需如何瀏覽器安全性設定會決定控制項是否會下載和顯示的憑證詳細資料。  
  
 已簽署之後尚未變更數位簽章可保證程式碼。 程式碼的雜湊是採取，而且內嵌在憑證中。 此雜湊是取自下載程式碼後，但它會執行程式碼的雜湊與進行比較。 Verisign 公司可以提供簽署程式碼所需的私人和公用金鑰。 ActiveX SDK 隨附 MakeCert 的公用程式建立測試憑證。  
  
##  <a name="_core_managing_the_palette"></a>管理調色盤  
 容器判斷調色盤，並將其做為環境的屬性，提供**DISPID_AMBIENT_PALETTE**。 容器 (例如，Internet Explorer) 選擇調色盤頁面上的所有 ActiveX 控制項用來判斷它們自己的調色盤。 如此可防止顯示閃爍，並提供一致的外觀。  
  
 控制項可以覆寫`OnAmbientPropertyChange`處理的調色盤變更通知。  
  
 控制項可以覆寫`OnGetColorSet`傳回設繪製調色盤的色彩。 容器會使用傳回的值，以判斷控制項是否調色盤感知。  
  
 下 OCX 96 指導方針，控制項必須一律會了解其在背景中的調色盤。  
  
 不要使用環境的調色盤屬性的舊容器將會傳送`WM_QUERYNEWPALETTE`和`WM_PALETTECHANGED`訊息。 控制項可以覆寫`OnQueryNewPalette`和`OnPaletteChanged`來處理這些訊息。  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Internet Explorer 瀏覽器安全性層級和控制行為  
 在瀏覽器的安全性層級，可由使用者設定的選項。 網頁可能包含作用中的內容可能會傷害使用者的電腦，因為瀏覽器會允許使用者選取安全性層級的選項。 根據瀏覽器實作的安全性層級的方式，控制項可能不完全下載，或憑證或警告訊息，讓使用者在執行階段選擇要下載此控制項將會顯示。 高、 中、 低安全性等級下在 Internet Explorer 的 ActiveX 控制項的行為如下所示。  
  
### <a name="high-safety-mode"></a>高安全性模式  
  
-   不帶正負號的控制項不會下載。  
  
-   如果未受信任的已簽署的控制項將顯示憑證 （使用者可以選擇此選項以永遠信任這個憑證擁有者的程式碼從現在起）。  
  
-   標示為安全的控制項將會有持續性資料中且/或可編寫指令碼。  
  
### <a name="medium-safety-mode"></a>中度的安全性模式  
  
-   不帶正負號的控制項將會顯示在下載之前的警告。  
  
-   帶正負號的控制項將顯示不受信任的憑證。  
  
-   未標示為安全的控制項將會顯示警告。  
  
### <a name="low-safety-mode"></a>低安全性模式  
  
-   下載控制項時，而不發出警告。  
  
-   發生指令碼處理和持續性，而不發出警告。  
  
## <a name="see-also"></a>請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [MFC ActiveX 控制項：授權 ActiveX 控制項](../mfc/mfc-activex-controls-licensing-an-activex-control.md)


---
title: "C++ 精靈的 JScript 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "精靈 JScript 方法"
  - "精靈 JScript 方法, 建立 C++ 精靈"
ms.assetid: f3046c56-cf67-4aaa-919e-8c066bfb6760
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 精靈的 JScript 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

|||  
|-|-|  
|[AddATLSupportToProject](../ide/addatlsupporttoproject.md)|將 ATL 支援加入至 MFC 專案中。|  
|[AddCoclassFromFile](../ide/addcoclassfromfile.md)|將包含 coclass 的樣板檔轉譯 \(Render\) 並插入至專案的 .idl 檔中。|  
|[AddCommonConfig](../ide/addcommonconfig.md)|將預設組態加入至專案中。|  
|[AddFilesToProject](../ide/addfilestoproject.md)|根據 Templates.inf 檔中的清單，將其中所有的檔案加入至專案中。|  
|[AddInterfaceFromFile](../ide/addinterfacefromfile.md)|將包含介面的樣板檔轉譯並插入至專案的 IDL 檔中。|  
|[CanAddATLClass](../ide/canaddatlclass.md)|由精靈所呼叫的函式，用來驗證專案是否與將要執行的程式碼精靈相容 \(換句話說，它可以接受 ATL 類別\)。<br /><br /> 當 PREPROCESS\_FUNCTION 參數位於[專案控制項的 .vsz 檔](../ide/dot-vsz-file-project-control.md)內時，精靈會呼叫這個函式，並檢查是否可使用 [Visual C\+\+ Code Model](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b)。  如果無法使用此程式碼模型，則函式將報告錯誤並傳回 **false**。|  
|[CanAddClass](../ide/canaddclass.md)|當 PREPROCESS\_FUNCTION 參數位於專案控制項的 .vsz 檔內時，精靈會呼叫這個函式。<br /><br /> 它會驗證 Visual C\+\+ 程式碼模型物件是否可用。  如果無法使用此程式碼模型，則函式將報告錯誤並傳回 **false**。|  
|[CanAddMFCClass](../ide/canaddmfcclass.md)|由精靈所呼叫的函式，用來驗證專案與將要執行的程式碼精靈是否相容 \(也就是說，它可以接受 MFC 類別\)。<br /><br /> 當 PREPROCESS\_FUNCTION 參數位於專案控制項的 .vsz 檔內時，精靈會呼叫這個函式，並檢查 Visual C\+\+ 程式碼模型物件是否可用。  如果無法使用此程式碼模型，則函式將報告錯誤並傳回 **false**。|  
|[CanAddNonAttributed](../ide/canaddnonattributed.md)|表示專案是否同時支援屬性化和非屬性化的 ATL 物件。|  
|[CanUseFileName](../ide/canusefilename.md)|檢查檔案是否存在。  如果存在，則精靈會提示使用者將程式碼合併以加入至現有的檔案中。|  
|[ConvertProjectToAttributed](../ide/convertprojecttoattributed.md)|將 ATL 專案轉換為屬性化。|  
|[CreateInfFile](../ide/createinffile.md)|建立 Templates.inf 檔。|  
|[CreateProject](../ide/createproject.md)|建立 C\+\+ 專案。|  
|[CreateSafeName](../ide/createsafename.md)|產生 C\+\+ 易記名稱。|  
|[DeleteFile](../ide/deletefile.md)|刪除指定的檔案。|  
|[DoesIncludeExist](../ide/doesincludeexist.md)|表示檔案中是否存在 `#include` 陳述式 \(Statement\)。|  
|[GetCodeForDllCanUnloadNow](../ide/getcodefordllcanunloadnow.md)|擷取卸載 DLL 所需的程式碼。|  
|[GetCodeForDllGetClassObject](../ide/getcodefordllgetclassobject.md)|擷取 DLL 類別物件的程式碼。|  
|[GetCodeForDllRegisterServer](../ide/getcodefordllregisterserver.md)|擷取登錄伺服器的程式碼。|  
|[GetCodeForDllUnregisterServer](../ide/getcodefordllunregisterserver.md)|擷取移除登錄伺服器的程式碼。|  
|[GetCodeForExitInstance](../ide/getcodeforexitinstance.md)|取得 `ExitInstance` 文字的 Helper 函式。|  
|[GetCodeForInitInstance](../ide/getcodeforinitinstance.md)|取得 [InitInstance](../Topic/CWinApp::InitInstance.md) 文字的 Helper 函式。|  
|[GetExportPragmas](../ide/getexportpragmas.md)|擷取匯出函式的 pragma。|  
|[GetInterfaceClasses](../ide/getinterfaceclasses.md)|傳回與介面相關聯的 `VCCodeClass` 物件。|  
|[GetInterfaceType](../ide/getinterfacetype.md)|傳回介面的型別 \(例如 Custom、Dual、Dispinterface 和 Oleautomation\)。|  
|[GetMaxID](../ide/getmaxid.md)|由此介面的成員和其所有基底，傳回最大的 `dispid`。|  
|[GetMemberfunction](../ide/getmemberfunction.md)|根據指定的名稱傳回函式物件。|  
|[GetProjectFile](../ide/getprojectfile.md)|傳回每個專案檔案類型的檔名 \(.rc 和.idl 等等\)。|  
|[GetProjectPath](../ide/getprojectpath.md)|傳回專案的目錄路徑。|  
|[GetRuntimeErrorDesc](../ide/getruntimeerrordesc.md)|傳回例外狀況 \(Exception\) 類型的描述。|  
|[GetUniqueFileName](../ide/getuniquefilename.md)|傳回唯一的檔名。|  
|[IncludeCodeElementDeclaration](../ide/includecodeelementdeclaration.md)|將 Include 陳述式加入至 `strInFile`，如果專案中找得到此標頭的話，則也包含實作 `strCodeElemName` 的標頭。|  
|[InsertIntoFunction](../ide/insertintofunction.md)|在 `AddATLSupportToProject` 中所呼叫的 Helper 函式，用來將程式碼插入至 `InitInstance`。|  
|[IsATLProject](../ide/isatlproject.md)|表示專案是否為 ATL 架構。|  
|[IsAttributedProject](../ide/isattributedproject.md)|表示專案是否為屬性化。|  
|[IsMFCProject](../ide/ismfcproject.md)|檢查專案是否為 MFC 架構。|  
|[LineBeginsWith](../ide/linebeginswith.md)|在 `InsertIntoFunction` 中所呼叫的 Helper 函式，用來判斷一行是否以特定的字串開始。|  
|[OffsetToLineNumber](../ide/offsettolinenumber.md)|尋找函式主體內指定位置的行號。|  
|[OnWizFinish](../ide/onwizfinish.md)|當使用者按一下 \[完成\] 時，由精靈 HTML 指令碼所呼叫的函式。  呼叫此精靈控制項的 **Finish** 方法。|  
|[RenderAddTemplate](../ide/renderaddtemplate.md)|轉譯樣板檔並選擇性地將其加入至專案中。|  
|[SetCommonPchSettings](../ide/setcommonpchsettings.md)|設定專案的先行編譯標頭 \(Precompiled Header\)。|  
|[SetErrorInfo](../ide/seterrorinfo.md)|提供錯誤資訊。|  
|[SetFilters](../ide/setfilters.md)|加入專案資料夾的來源 \(Source\)、包含 \(Include\) 和資源 \(Resource\) 篩選條件。|  
|[SetMergeProxySymbol](../ide/setmergeproxysymbol.md)|由精靈所呼叫，以便在必要時加入 \_MERGE\_PROXYSTUB 符號。|  
|[SetNoPchSettings](../ide/setnopchsettings.md)|於未使用先行編譯標頭時，設定專案組態屬性。|  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
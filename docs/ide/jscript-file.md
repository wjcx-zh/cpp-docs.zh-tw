---
title: "JScript 檔案 | Microsoft Docs"
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
  - "AddConfig 方法"
  - "AddFilesToCustomProj 方法"
  - "AddFilters 方法"
  - "Common.js 檔案"
  - "CreateCustomInfFile 方法"
  - "CreateCustomProject 方法"
  - "自訂精靈, 存取精靈物件模型"
  - "自訂精靈, JScript 檔案"
  - "偵錯 [JScript], 啟用指令碼偵錯"
  - "偵錯 [JScript], JScript 檔案"
  - "偵錯指令碼"
  - "偵錯指令碼, 啟用指令碼偵錯"
  - "Default.js 檔案"
  - "DelFile 方法"
  - "檔案 [C++], 由自訂精靈建立"
  - "GetTargetName 方法"
  - "JScript 檔案"
  - "OnFinish 方法"
  - "PchSettings 方法"
ms.assetid: 7841a09e-2dd2-4f1a-a13a-39ac53f24315
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# JScript 檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[自訂精靈](../ide/custom-wizard.md)會針對每個專案，存取指令碼引擎，並建立名為 Default.js 的 JScript 檔。  它也包含了 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)。  這些檔案包含 JScript 函式，其讓您可存取 Visual Studio 和 Visual C\+\+ 物件模型來自訂精靈   \(如需這些模型的清單，請參閱[設計精靈](../ide/designing-a-wizard.md)\)。 您可將自己的函式加入至精靈專案的 Default.js 檔中。  若要存取精靈物件模型中的屬性和方法，或是存取 JScript 檔中的環境模型，請在物件模型項目前面分別加上 "wizard." 和 "dte."。  
  
 例如：  
  
```  
function CreateCustomProject(strProjectName, strProjectPath)  
{  
   try  
   {  
      var strProjTemplatePath = wizard.FindSymbol('PROJECT_TEMPLATE_PATH');  
var strProjTemplate = '';  
      strProjTemplate = strProjTemplatePath + '\\default.vcproj';  
  
      var Solution = dte.Solution;  
      var strSolutionName = "";  
      if (wizard.FindSymbol("CLOSE_SOLUTION"))  
...  
```  
  
 當您在[自訂精靈](../ide/custom-wizard.md)中按一下 \[完成\] 時，精靈會在 \[方案總管\] 中的 \[指令碼檔\] 資料夾中載入 Default.js 檔案。  這個 JScript 檔即建立專案並轉譯該樣板，之後當使用者在您的精靈中按一下 \[完成\] 時，便會將它們加入至 \[方案總管\]。  
  
 根據預設，專案的 Default.js 檔包含下列函式：  
  
|函式名稱|描述|  
|----------|--------|  
|**AddConfig**|加入專案的組態。  您可提供編譯器 \(Compiler\) 和連結器 \(Linker\) 設定。|  
|**AddFilesToCustomProj**|當使用者按一下 \[完成\] 時，將指定的檔案加入至專案。|  
|**AddFilters**|當使用者按一下 \[完成\] 時，將指定的來源篩選器加入至專案。|  
|**CreateCustomProject**|當使用者按一下 \[完成\] 時，便會在指定位置建立該專案。|  
|**CreateCustomInfFile**|建立專案的 [Templates.inf 檔案](../ide/templates-inf-file.md)。|  
|**DelFile**|刪除指定的檔案。|  
|**GetTargetName**|取得指定檔案名稱。|  
|**OnFinish**|在使用者按一下 \[完成\] 時由精靈所呼叫，以便建立專案、加入檔案和篩選器、轉譯範本，以及設定組態。|  
|**PchSettings**|設定先行編譯標頭設定值。  如需詳細資訊，請參閱 Common.js 參考中的 [SetCommonPchSettings](../ide/setcommonpchsettings.md)。|  
  
 每一個精靈都有一個唯一的 Default.js 檔，其包含 TODO 註解，以協助您辨識必須自訂檔案的地方。  
  
 Visual C\+\+ 並包含 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)，它是一個可供所有精靈共用的檔案，並內含於您的精靈專案中。  您可使用 Common.js 中的函式。  
  
> [!NOTE]
>  Common.js 包含每個函式和其參數的說明。  如需詳細資訊，請參閱 Common.js 中的註解。  
  
 如果您有想要供精靈專案共用的函式，您可將它們加入至 Common.js。  請建立您自己的 Common.js 版本，並將它儲存在通用路徑中，然後在您的 [.vsz 檔案](../ide/dot-vsz-file-project-control.md)中將 SCRIPT\_COMMON\_PATH 設成這個路徑。  
  
> [!NOTE]
>  Visual C\+\+ 內附的精靈使用 Common.js 中的 JScript 函式。  如果您變更這些函式，Visual C\+\+ 精靈可能無法如預期般運作。  
  
 如需 JScript 的詳細資訊，請參閱[Writing, Compiling, and Debugging JScript Code](http://msdn.microsoft.com/zh-tw/13e57e7d-4867-4555-b9e4-fc24aa75e628)。  
  
## 偵錯指令  
 若要偵錯精靈 html 檔案中的指令，您必須啟用指令偵錯。  
  
#### 若要啟用指令碼偵錯  
  
1.  按一下 Internet Explorer 的 \[工具\] 功能表，並選擇 \[**網際網路選項**\]。  
  
2.  按一下 \[**進階**\] 索引標籤。  
  
3.  清除 \[瀏覽\] 分類下的 \[關閉 Script 偵錯\] 核取方塊。  
  
 這樣也可以在按一下精靈的 \[完成\] 按鈕時，讓 common.js 和 default.js 出現在 \[**執行中的文件**\] 視窗中。  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
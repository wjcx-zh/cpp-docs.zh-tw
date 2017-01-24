---
title: "/w、/Wn、/WX、/Wall、/wln、/wdn、/wen、/won (警告層級) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.DisableSpecificWarnings"
  - "VC.Project.VCCLCompilerTool.WarningLevel"
  - "VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings"
  - "VC.Project.VCCLCompilerTool.WarnAsError"
  - "VC.Project.VCCLWCECompilerTool.WarnAsError"
  - "/wx"
  - "VC.Project.VCCLWCECompilerTool.WarningLevel"
  - "/wall"
  - "VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors"
  - "/Wv"
  - "/w0"
  - "/w1"
  - "/w2"
  - "/w3"
  - "/w4"
  - "/wd"
  - "/we"
  - "/wo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/w 編譯器選項"
  - "/W0 編譯器選項 [C++]"
  - "/W1 編譯器選項 [C++]"
  - "/W2 編譯器選項 [C++]"
  - "/W3 編譯器選項 [C++]"
  - "/W4 編譯器選項 [C++]"
  - "/Wall 編譯器選項 [C++]"
  - "/wd 編譯器選項 [C++]"
  - "/we 編譯器選項 [C++]"
  - "/wo 編譯器選項 [C++]"
  - "/WX 編譯器選項 [C++]"
  - "w 編譯器選項 [C++]"
  - "-w 編譯器選項 [C++]"
  - "W0 編譯器選項 [C++]"
  - "-W0 編譯器選項 [C++]"
  - "W1 編譯器選項 [C++]"
  - "-W1 編譯器選項 [C++]"
  - "W2 編譯器選項 [C++]"
  - "-W2 編譯器選項 [C++]"
  - "W3 編譯器選項 [C++]"
  - "-W3 編譯器選項 [C++]"
  - "W4 編譯器選項 [C++]"
  - "-W4 編譯器選項 [C++]"
  - "Wall 編譯器選項 [C++]"
  - "-Wall 編譯器選項 [C++]"
  - "警告層級編譯器選項"
  - "警告, 以編譯器選項視為錯誤"
  - "wd 編譯器選項 [C++]"
  - "-wd 編譯器選項 [C++]"
  - "we 編譯器選項 [C++]"
  - "-we 編譯器選項 [C++]"
  - "wo 編譯器選項 [C++]"
  - "-wo 編譯器選項 [C++]"
  - "WX 編譯器選項 [C++]"
  - "-WX 編譯器選項 [C++]"
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /w、/Wn、/WX、/Wall、/wln、/wdn、/wen、/won (警告層級)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定編譯器如何對指定的編譯產生警告。  
  
## 語法  
  
```  
/w  
/Wn  
/WX  
/Wall  
/wln  
/wdn  
/wen  
/won  
```  
  
## 備註  
 下表中描述可用的選項和相關引數。  
  
|選項|說明|  
|--------|--------|  
|**\/w**|停用所有編譯器警告。|  
|**\/W** `n`|指定編譯器要產生的警告層級。  `n` 範圍的有效警告層級是從 0 到 4：<br /><br /> -   層級 0 停用所有警告。<br />-   層級 1 顯示嚴重警告。  預設的設定值是層級 1。<br />-   層級 2 顯示所有層級 1 警告，以及嚴重性不及層級 1 的警告。<br />-   層級 3 顯示所有層級 2 警告以及對生產用途建議的所有其他警告。<br />-   層級 4 顯示警告層級 3 及某些資訊警告。  建議您使用這個選項只提供像紙毛的警告。  然而對於新專案，最好在所有編譯中都使用 `/W4`；解除所有警告可以確保將不易發現的程式碼缺點降低到最少程度。|  
|**\/Wall**|顯示預設在 \/W4 不包含—例如，警告關閉的所有 \/W4 警告和其他警告。  請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|  
|**\/WX**|將所有編譯器警告視為錯誤。  對於新專案，最好在所有編譯中都使用 **\/WX**；解除所有警告可以確保將不易發現的程式碼缺點降低到最少程度。<br /><br /> 連結器也有 **\/WX** 選項。  如需詳細資訊，請參閱[\/WX \(將連結器警告視為錯誤\)](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|  
|**\/w** `ln`|指定特定警告的層級。  第一個參數是設定警告層級 \(與 **\/W**`n` 相同\) 而第二個參數則是實際的警告編號。<br /><br /> 例如，`/w14326` 會使 C4326 成為層級 1 警告。|  
|**\/wd** `n`|會在 `n`指定的編譯器警告。<br /><br /> 例如，`/wd4326` 會停用編譯器警告 C4326。|  
|**\/we** `n`|要視為錯誤的 `n`中指定的編譯器警告。<br /><br /> 例如，`/we4326` 會將警告號碼 C4326 標記為錯誤。|  
|**\/wo** `n`|只報告一次錯誤在 `n`指定的編譯器警告。<br /><br /> 例如，`/wo4326` 會使警告 C4326 只被報告一次。|  
  
 如果您以 **\/w** 的其中一個選項建立先行編譯標頭 \([\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md)\)，則只要使用此先行編譯標頭 \([\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)\) 都會讓同樣的 **\/w** 選項再作用一次。  您可以在命令列以另一個 **\/w** 選項覆寫先行編譯標頭中的 **\/w** 設定。  
  
 在原始程式碼中的 Pragma 指示詞不會受 **\/w** 選項的影響。  
  
 您也可以使用 [warning](../../preprocessor/warning.md)，控制在編譯時期報告的警告層級。  
  
 [建置錯誤資料](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) 描述警告和警告層級和表示某些陳述式為何無法進行編譯。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\]。  
  
3.  在 \[**一般**\] 屬性頁，並且修改 \[**警告層級**\] 或 \[**警告視為錯誤**\] 屬性。  
  
4.  在 \[**進階**\] 屬性頁並且修改 \[**停用特定警告**\] 屬性。  
  
5.  對於其餘的選項，在 \[**命令列**\] 屬性頁，並且在 \[**其他選項**\] 方塊中輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
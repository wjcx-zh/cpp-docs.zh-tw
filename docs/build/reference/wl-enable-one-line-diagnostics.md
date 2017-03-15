---
title: "/WL (啟用一行診斷) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/wl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/WL 編譯器選項 [C++]"
  - "WL 編譯器選項 [C++]"
  - "-WL 編譯器選項 [C++]"
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /WL (啟用一行診斷)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

附加額外資訊至錯誤或警告訊息。  
  
## 語法  
  
```  
/WL  
```  
  
## 備註  
 C\+\+ 編譯器的錯誤和警告訊息後面可以接著 \(預設\) 出現在另一新行中的其他資訊。  當您從命令列編譯時，可以附加額外的一行資訊到錯誤或警告訊息上。  如果您要將組建 \(Build\) 輸出擷取到一個記錄檔然後再處理這個記錄檔來找出所有錯誤和警告的話，這可能很適合您的需要。  分號會將錯誤或警告訊息與這個額外行隔開。  
  
 並非所有錯誤和警告訊息都有額外的一行資訊。  下列程式碼會產生有一行額外資訊的錯誤；它可以讓您測試使用 **\/WL** 時的效果。  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
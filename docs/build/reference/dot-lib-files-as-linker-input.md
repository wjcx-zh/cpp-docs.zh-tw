---
title: ".Lib 檔做為連結器輸入 | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.AdditionalDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".lib 檔案"
  - "COFF 檔案, 匯入程式庫"
  - "預設程式庫 [C++]"
  - "預設程式庫 [C++], 連結器輸出"
  - "預設值 [C++], 程式庫"
  - "匯入程式庫, 連結器檔案"
  - "程式庫 [C++], .lib 檔做為連結器輸入"
  - "連結 [C++], OMF 程式庫"
  - "OMF 程式庫"
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Lib 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK 可以接受 COFF 標準程式庫及 COFF 匯入程式庫，這兩者通常都具有 .lib 副檔名。  標準程式庫含有一些目的檔，而且是由 LIB 工具建立的。  匯入程式庫含有關於其他程式匯出的資訊，而且是由 LINK 在建置含有匯出之程式時所建立或由 LIB 工具所建立。  如需有關使用 LIB 建立標準或匯入程式庫的詳細資訊，請參閱 [LIB 參考](../../build/reference/lib-reference.md)。  如需有關使用 LINK 建立匯入程式庫的詳細資訊，請參閱 [\/DLL](../../build/reference/dll-build-a-dll.md) 選項。  
  
 程式庫是做為檔名引數或預設程式庫指定到 LINK。  LINK 解析外部參考的方式是首先搜尋命令列上指定的程式庫，接著再搜尋以 [\/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) 選項指定的預設程式庫，然後再搜尋 .obj 檔中所命名的預設程式庫。  如果程式庫名稱指定了路徑，LINK 便會在那個目錄中尋找程式庫。  如果沒有指定路徑，LINK 會首先尋找執行 LINK 的目錄，然後再搜尋 LIB 環境變數中所指定的任何目錄。  
  
### 在開發環境中加入 .lib 檔做為連結器輸入  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[輸入\] 屬性頁。  
  
4.  修改 \[**其他相依性**\] 屬性。  
  
### 以程式設計方式加入 .lib 檔做為連結器輸入  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalDependencies%2A>。  
  
## 範例  
 以下範例會示範如何建置及使用 .lib 檔：  
  
```  
// lib_link_input_1.cpp  
// compile with: /LD  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
## 範例  
 然後：  
  
```  
// lib_link_input_2.cpp  
// compile with: /EHsc lib_link_input_1.lib  
__declspec(dllimport) int Test();  
#include <iostream>  
int main() {  
   std::cout << Test() << std::endl;  
}  
```  
  
  **213**   
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)
---
title: "/Zc:wchar_t (wchar_t 是原生類型) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType"
  - "VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType"
  - "/Zc:wchar_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 編譯器選項 [C++]"
  - "Conformance 編譯器選項"
  - "wchar_t 類型"
  - "Zc 編譯器選項 [C++]"
  - "-Zc 編譯器選項 [C++]"
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /Zc:wchar_t (wchar_t 是原生類型)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

根據 C\+\+ 標準將 `wchar_t` 解析為內建類型。  **\/Zc:wchar\_t** 依預設為開啟。  
  
## 語法  
  
```  
/Zc:wchar_t[-]  
```  
  
## 備註  
 如果 **\/Zc:wchar\_t** 已開啟，則 `wchar_t` 會對應至 Microsoft 特定原生類型 `__wchar_t`。  如果指定 **\/Zc:wchar\_t\-** \(具減號\)，則 `wchar_t` 會對應至 `unsigned short` 的 `typedef`。  \(在 Visual C\+\+ 6.0 和之前版本中，`wchar_t` 並未實作為內建類型，而是在 wchar.h 中宣告為 `unsigned short` 的 `typedef`\)。因為 C\+\+ 標準要求 `wchar_t` 必須是內建類型，因此我們不建議 **\/Zc:wchar\_t\-**。  使用 `typedef` 版本可能會造成可攜性問題。  如果您是從舊版的 Visual C\+\+ 升級，並且因為程式碼嘗試以隱含方式將 `wchar_t` 轉換成 `unsigned short` 而遇到編譯器錯誤 [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)，我們建議您變更程式碼來修正錯誤，而不變更 **\/Zc:wchar\_t\-** 設定。  
  
 Microsoft 將 `wchar_t` 實作為二位元的不帶正負號值。  如需 `wchar_t`的詳細資訊，請參閱 [資料類型範圍](../../cpp/data-type-ranges.md)和 [基本類型](../../cpp/fundamental-types-cpp.md)。  
  
 如果您寫入的新程式碼必須與仍使用 `wchar_t` 的 `typedef` 版本的舊版程式碼交互操作，您可以為 `wchar_t` 的 `unsigned short` 和 `__wchar_t` 變化提供多載，如此您的程式碼就可以與使用或不使用 **\/Zc:wchar\_t** 進行編譯的程式碼進行連結。  否則，您必須提供兩個不同的程式庫組建，一個已啟用 **\/Zc:wchar\_t**，一個未啟用。  縱使在這種情況，我們仍然建議您以編譯新程式碼所使用的相同編譯器建置較舊的程式碼。  切勿混合不同編譯器所編譯的二進位檔。  
  
 當指定 **\/Zc:wchar\_t** 時，便會定義 **\_WCHAR\_T\_DEFINED** 和 **\_NATIVE\_WCHAR\_T\_DEFINED** 符號。  如需詳細資訊，請參閱[預先定義的巨集](../../preprocessor/predefined-macros.md)。  
  
 如果您的程式碼使用編譯器 COM 全域函式，由於 **\/Zc:wchar\_t** 現在預設為開啟，我們建議您將對 comsupp.lib 的明確參考從[註解 pragma](../../preprocessor/comment-c-cpp.md) 或命令列變更為 comsuppw.lib 或 comsuppwd.lib。  \(如果您必須使用 **\/Zc:wchar\_t\-** 進行編譯，請使用 comsupp.lib\)。如果您包括 comdef.h 標頭檔，則會為您指定正確的程式庫。  如需有關編譯器 COM 支援的詳細資訊，請參閱 [編譯器 COM 支援](../../cpp/compiler-com-support.md)。  
  
 當您編譯 C 程式碼時，不會支援 `wchar_t` 類型。  如需 Visual C\+\+ 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展開 \[**組態屬性**\]、\[**C\/C\+\+**\]，然後選取 \[**語言**\]。  
  
3.  修改 \[**將 wchar\_t 當做 Built\-in 類型**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)
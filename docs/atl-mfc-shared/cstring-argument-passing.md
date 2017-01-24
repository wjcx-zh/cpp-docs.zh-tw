---
title: "CString Argument Passing | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argument passing [C++]"
  - "argument passing [C++], C strings"
  - "arguments [C++], 傳遞"
  - "CString objects, 傳遞引數"
  - "函式 [C++], strings as input/output"
  - "傳遞引數, C strings"
  - "string arguments"
  - "字串 [C++], as function input/output"
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CString Argument Passing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件說明如何傳遞至函式的 [CString](../atl-mfc-shared/reference/cstringt-class.md) 物件以及如何從函式傳回 `CString` 物件。  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString 引數傳遞給方法的慣例  
 當您定義類別介面時，您必須決定您的成員函式的引數傳遞給方法的慣例。  會傳遞和傳回的物件 `CString` 某些標準規則。  如果您遵循此 [當輸入字串函式](#_core_strings_as_function_inputs) 和 [當字串函式輸出](#_core_strings_as_function_outputs)說明的規則，則會有更有效率，正確的程式碼。  
  
##  <a name="_core_strings_as_function_inputs"></a> 當輸入字串函式  
 最有效率且最安全的方式使用 `CString` 物件在呼叫的函式會傳遞至函式的 `CString` 物件。  儘管這個名稱， `CString` 物件內部沒有儲存字串時有 null 結束字元的 C\+\+. 格式的樣式。  相反地， `CString` 物件保存它有字元數的謹慎地追蹤。  具有 `CString` 供具 `LPCTSTR` 指標的 NULL 結尾字串可能變得相當大的少量工作，如果您的程式碼必須經常執行。  因為對 `CString` 內容進行任何變更失效 `LPCTSTR` 指標，舊複本結果是暫時的。  
  
 因此才會在特定情況下提供 C\+\+. 格式的樣式。  例如，可能有所呼叫函式以 C 撰寫的狀況，並不支援物件。  在這種情況下，請強制 `CString` 參數設定為， `LPCTSTR`，而且函式會取得 . C 樣式以 null 結尾的字串。  您也可以移至另一個方向和建立 `CString` 物件使用接受 . C 樣式字串參數的 `CString` 建構函式。  
  
 如果字串內容要被函式變更，請為非常數 `CString` 參考 \(**CString\_&**\) 宣告參數。  
  
##  <a name="_core_strings_as_function_outputs"></a> 當字串函式輸出  
 通常，因為 `CString` 物件後面的類似基本型別的值，語意。您可以從函式傳回 `CString` 物件。  若要傳回唯讀字串，請使用常數 `CString` 參考 \(**const CString\_&**\)。  下列範例說明如何使用 `CString` 參數和傳回型別:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/CPP/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/CPP/cstring-argument-passing_2.cpp)]  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)
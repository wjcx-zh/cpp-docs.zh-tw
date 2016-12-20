---
title: "Using CString | Microsoft Docs"
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
  - "CString class (Visual C++)"
  - "CString objects, C++ string manipulation"
  - "CString objects, reference counting"
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using CString
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節中的主題會描述如何使用 `CString` 進行程式設計。  如需 `CString` 類別的參考文件，請參閱 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 文件。  
  
 若要使用 `CString`，請包括 `atlstr.h` 標頭。  
  
 基於 `CString`、`CStringA` 和 `CStringW` 類別所支援的字元資料類型，這些類別是稱為 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 之類別樣板的特製化。  
  
 `CStringW` 物件包含 `wchar_t` 類型，且支援 Unicode 字串。  `CStringA` 物件包含 `char` 類型，且支援單一位元組和多位元組 \(MBCS\) 字串。  `CString` 物件支援 `char` 類型或 `wchar_t` 類型，具體取決於編譯時是定義 `MBCS` 符號，還是 `UNICODE` 符號。  
  
 `CString` 物件會在 `CStringData` 物件中保留字元資料。  `CString` 接受 `null` 結尾 C 樣式字串，但不會在已儲存的字元資料中保留 `null` 字元。  相反地，`CString` 會追蹤字串長度。  `CString` 在匯出 C 樣式字串時提供 null 結束字元。  您可以在 `CString` 中插入 `null`，但它可能會產生未預期的結果。  
  
 使用下列字串類別集時，可以不連結 MFC 程式庫、及具有或不具有 CRT 支援：`CAtlString`、`CAtlStringA` 和 `CAtlStringW`。  
  
 `CString` 在原生專案中使用。  對於 Managed 程式碼 \(C\+\+\/CLI\) 專案，請使用 `System::String`。  
  
 若要加入比 `CString`、`CStringA` 或 `CStringW` 目前提供的更多功能，您應該建立包含其他功能的 `CStringT` 子類別。  
  
 下列程式碼會顯示如何建立 `CString`，且將其列印至標準輸出：  
  
```cpp  
#include <atlstr.h>  
  
int main() {  
    CString aCString = CString(_T("A string"));  
    _tprintf(_T("%s"), (LPCTSTR) aCString);  
}  
```  
  
## 在本節中  
 [基本 CString 運算](../atl-mfc-shared/basic-cstring-operations.md)  
 描述基本 `CString` 作業，包括從 C 常值字串建立物件，存取 `CString` 中的個別字元，串連兩個物件，以及比較 `CString` 物件。  
  
 [字串資料管理](../atl-mfc-shared/string-data-management.md)  
 討論如何將 Unicode 及 MBCS 與 `CString` 搭配使用。  
  
 [CString 語意](../atl-mfc-shared/cstring-semantics.md)  
 解釋如何使用 `CString` 物件。  
  
 [與 C 樣式字串相關的 CString](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
 描述如何使用類似 C 樣式 null 結尾字串的方式，來操作 `CString` 物件的內容。  
  
 [針對 BSTR 配置及釋放記憶體](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
 討論如何針對 `BSTR` 及 COM 物件使用記憶體。  
  
 [CString 例外狀況清除](../atl-mfc-shared/cstring-exception-cleanup.md)  
 解釋 MFC 3.0 及以後版本中不再需要明確清除。  
  
 [CString 引數傳遞](../atl-mfc-shared/cstring-argument-passing.md)  
 解釋如何將 CString 物件傳遞至函式，以及如何從函式傳回 `CString` 物件。  
  
 [Unicode 及多位元組字元子集 \(MBCS\) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
 討論如何針對 Unicode 及 MBCS 支援啟用 MFC。  
  
## 參考  
 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 提供 `CStringT` 類別的參考資訊。  
  
 [CSimpleStringT Class](../atl-mfc-shared/reference/csimplestringt-class.md)  
 提供 `CSimpleStringT` 類別的參考資訊。  
  
## 相關章節  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)  
 包含各主題的連結，描述管理字串資料的數個方法。  
  
 [類別樣板具現化](../Topic/Class%20Template%20Instantiation.md)  
 `CString` 是基於 `CStringT` 的 `typedef`，其為類別樣板特製化的執行個體。
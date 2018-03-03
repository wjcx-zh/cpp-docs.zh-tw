---
title: "連結器工具錯誤 LNK2022 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ca45ed3cd83a3fc81a6dad8fdcec5aee3232c6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2022"></a>連結器工具錯誤 LNK2022  
  
> 中繼資料作業失敗 (*HRESULT*): *error_message*  
  
連結器合併中繼資料時發現錯誤。 已成功連結，必須先解決中繼資料錯誤。  
  
若要診斷此問題的一個方式就是執行**ildasm-語彙基元**在目的檔，尋找有哪些類型的語彙基元列在  `error_message`，並尋找差異。  中繼資料內具有相同名稱的兩種不同類型不正確，即使只是 LayoutType 屬性不同。  
  
其中一個原因 LNK2022 時的類型 （例如結構） 存在於多個編譯單位同名，但具有衝突的定義，以及當您使用編譯[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  在此情況下，請確定類型具有完全相同的定義，在所有編譯中。  型別名稱會列在`error_message`。  
  
連結器會尋找在不同位置的中繼資料檔案超過已指定給編譯器時，另一個可能的原因為 LNK2022 (與[#using](../../preprocessor/hash-using-directive-cpp.md) )。 確保中繼資料檔 (.dll 或 .netmodule) 所在位置是與傳遞給連結器時相同，也與傳遞給編譯器時相同。  
  
建置 ATL 應用程式，使用巨集時`_ATL_MIXED`需要在所有編譯中，如果至少一個使用它。  
  
## <a name="example"></a>範例  
  
下列範例會定義空的類型。  
  
```cpp  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>範例  
  
這個範例會顯示您無法連結兩個來源的程式碼檔案包含類型名稱相同但不同的定義。  
  
下列範例會產生 LNK2022。  
  
```cpp  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```
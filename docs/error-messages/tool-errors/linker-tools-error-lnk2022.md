---
title: "連結器工具錯誤 LNK2022 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 91fb85679fd6c66bc97974912a2de688f494d5e9
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2022"></a>連結器工具錯誤 LNK2022
中繼資料作業失敗 (HRESULT): error_message  
  
 連結器合併中繼資料時發現錯誤。 中繼資料錯誤必須解析成連結成功。  
  
 診斷此問題的方法之一是執行**ildasm – 語彙基元**上尋找有哪些類型的物件檔案的語彙基元列`error_message`，並尋找差異。  中繼資料，具有相同名稱的兩種不同類型不正確，即使只是 LayoutType 屬性不同。  
  
 其中一個原因 LNK2022 時 （例如結構） 的型別存在於多個編譯單位同名，但具有衝突的定義，而當您使用編譯[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  在此情況下，請確定該型別具有相同的定義，在所有編譯中。  類型名稱會列在`error_message`。  
  
 連結器會尋找在不同位置的中繼資料檔案於指定給編譯器時，另一個可能造成 LNK2022 (與[#using](../../preprocessor/hash-using-directive-cpp.md) )。 確保中繼資料檔 (.dll 或 .netmodule) 所在位置是與傳遞給連結器時相同，也與傳遞給編譯器時相同。  
  
 當建置 ATL 應用程式，使用[_ATL_MIXED](http://msdn.microsoft.com/Library/11b59a83-7098-43e2-9f7b-408299930966)需要在所有編譯中，如果它用在至少一個。  
  
## <a name="example"></a>範例  
 下列範例會定義空的型別。  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>範例  
 這個範例示範您無法連結兩個原始程式碼檔案包含型別的名稱相同但不同的定義。  
  
 下列範例會產生 LNK2022。  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```

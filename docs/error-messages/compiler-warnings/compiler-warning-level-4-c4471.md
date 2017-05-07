---
title: "編譯器警告 （層級 4） C4471 |Microsoft 文件"
ms.custom: 
ms.date: 04/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4471
dev_langs:
- C++
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
caps.latest.revision: 1
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
ms.sourcegitcommit: d7d097b399d3681ef523d8787ecc38af472840f6
ms.openlocfilehash: fc0ddb07ec768804be61185211bbac0ee6fbf2b6
ms.lasthandoff: 04/28/2017

---
# <a name="compiler-warning-level-4-c4471"></a>編譯器警告 （層級 4） C4471
'*列舉*': 不限範圍列舉的向前宣告必須含有基礎類型 (假設為 int)  
  
不限範圍列舉的向前宣告找不到沒有規範的基礎類型。 根據預設，Visual c + + 假設`int`是列舉的基礎類型。 如果使用不同類型是在列舉型別定義中，比方說，如果未指定不同的明確類型，或如果初始設定式隱含設定不同的型別，這會造成問題。 您可能也有可攜性問題;其他編譯器不會假設`int`是列舉型別的基礎型別。  
  
此警告預設為關閉。您可以使用 /Wall 或 /w*N*啟用在命令列，或使用 #pragma 4471[警告](../../preprocessor/warning.md)原始程式檔。  
  
在某些情況下，這項警告是假的。 如果向前宣告列舉類型出現在定義之後，可能會引發此警告。 比方說，這段程式碼是有效的即使它可能會造成 C4471:  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>範例  
一般情況下，它是安全使用於不限範圍而不是向前宣告列舉的完整定義。 您可以將定義放在標頭檔，並將它包括參考它的原始程式檔中。 這適用於 C + + 98 和更新版本所撰寫的程式碼。 我們建議此解決方案可攜性和維護的方便性。  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>範例  
在 C + + 11 中，您可以新增明確的類型，不限範圍列舉型別以及其向前宣告。 只有當複雜的標頭包含邏輯會防止使用而不是向前宣告的定義，我們建議此解決方案。 此方案可能會導致維護問題︰ 如果您變更用於列舉型別定義的基礎類型，您也必須變更以符合，向前宣告的所有或您的程式碼中可能有無訊息的錯誤。 您可以將向前宣告放入標頭檔，以減少此問題。  
  
```cpp  
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```  
  
```cpp  
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```  
  
如果您指定列舉類型的明確型別時，我們建議您也可以啟用警告[C4369](compiler-warning-level-1-C4369.md)，其預設為開啟。 這會識別需為列舉型別項目類型不同於明確指定類型的情況。
  
## <a name="example"></a>範例  
您可以變更您的程式碼使用的限定範圍的列舉，在 C + + 11 的新功能。 定義和使用列舉類型的任何用戶端程式碼，都必須變更為使用限定範圍的列舉。 我們建議您使用限定範圍的列舉有問題的命名空間的侵害，因為列舉的範圍限於定義的列舉項目的名稱。 限定範圍列舉的另一個功能是其成員無法隱含地轉換成另一個整數或列舉類型，這可能會出現細微的 bug 的來源。

```cpp  
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```  
  
```cpp  
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```  
  


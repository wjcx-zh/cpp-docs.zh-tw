---
title: "編譯器警告 （層級 1） C4691 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4691
dev_langs:
- C++
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17673ee3e65d2e0cd0d989c56759b62de38f5fdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4691"></a>編譯器警告 (層級 1) C4691
'type': 未參考組件 'file'，而是會使用目前的轉譯單位中定義的型別中，必須有參考類型  
  
 未參考包含原始型別定義的中繼資料檔案，且編譯器使用區域類型定義。  
  
 在您重建的情況下*檔案*，可以略過或關閉使用 pragma C4691[警告](../../preprocessor/warning.md)。  也就是說，如果您要建置的檔案是相同的編譯器會找不到型別定義預期的檔案，您可以忽略 C4691。  
  
 不過，如果編譯器會使用的定義，不是來自相同的組件所參考的中繼資料，可能會發生未預期的行為CLR 型別具有型別名稱的型別，不僅可以也由組件。  也就是從組件 z.dll Z 類型是不同於從組件 y.dll 類型 Z。  
  
## <a name="example"></a>範例  
 此範例包含原始型別定義。  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## <a name="example"></a>範例  
 此範例會參考 C4691_a.dll 和宣告類型 Original_Type 的欄位。  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C4691。  請注意此範例包含 Original_Type 定義，且未參考 C4691a.dll。  
  
 若要解決，參考包含原始型別定義的中繼資料檔案而移除的區域宣告和定義。  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```
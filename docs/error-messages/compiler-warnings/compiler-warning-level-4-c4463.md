---
title: "編譯器警告 （層級 4） C4463 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4463
dev_langs: C++
helpviewer_keywords: C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71b438de515a4fd01e7714de685ee0a89adb609e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4463"></a>編譯器警告 （層級 4） C4463  
  
> 溢位。指派*值*只能保留值的位元欄位*low_value*至*high_value*  
  
受指派*值*超出範圍的位元欄位可以保存的值。 帶正負號的位元欄位類型使用高位位元正負號，因此如果 *n* 是帶正負號的位元欄位是-2 的位元欄位的大小，範圍<sup>n-1</sup> 2<sup>n-1</sup>-1，而不帶正負號的位元欄位必須介於 0 到 2<sup>n</sup>-1。  
  
## <a name="example"></a>範例  
  
這個範例會產生 C4463，因為它會嘗試將 3 這個值指派給位元欄位的型別`int`大小為 2，擁有從-2 範圍為 1。  
  
若要修正此問題，您可以變更指派的值為允許的範圍中的項目。 如果位元欄位保存不帶正負號的值範圍從 0 到 3，您可以變更的宣告型別`unsigned`。 如果欄位為了儲存於範圍-4 到 3 的值，您可以將位元欄位大小變更為 3。  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  

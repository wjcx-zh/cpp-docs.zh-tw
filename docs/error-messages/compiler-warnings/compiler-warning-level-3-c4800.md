---
title: "編譯器警告 （層級 3） C4800 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4800
dev_langs: C++
helpviewer_keywords: C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 687b0dab996bfbfe2ce30d65b86196383c02b914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4800"></a>編譯器警告 (層級 3) C4800  
  
> '*類型*': 值強制設 bool 'true' 或 'false' （效能警告）  
  
值，並不會產生這個警告`bool`指派或強制轉型為類型`bool`。 一般而言，這個訊息藉由指派致`int`變數，以`bool`變數其中`int`變數只包含值**true**和**false**，而且可能會重新宣告為類型`bool`。 如果您不能重新撰寫運算式，以使用型別`bool`，接著您可以將新增 「`!=0`」 為運算式，可讓運算式型別`bool`。 將運算式轉換成輸入`bool`不停用警告，是設計所致。  
  
在 Visual Studio 2017 不再產生這個警告。  
  
## <a name="example"></a>範例
  
 下列範例會產生 C4800，並示範如何修正此問題：  
  
```cpp  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // To fix, instead try:  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```
---
title: "編譯器錯誤 C3445 |Microsoft 文件"
ms.custom: 
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e880eca87816973d531a2662486dde0ae7c77987
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3445"></a>編譯器錯誤 C3445
複本集的清單初始化 '*類型*' 不能使用明確的建構函式  
  
根據 ISO C + + 17 標準，編譯器需要考慮複製清單初始化中的多載解析的明確建構函式，但如果實際上選擇該多載，則必須引發錯誤。  
  
從 Visual Studio 2017 開始，編譯器會尋找使用初始設定式清單的物件建立相關的錯誤，找不到 Visual Studio 2015。 這些錯誤可能會導致損毀或未定義的行為在執行階段。

## <a name="example"></a>範例  
 下列範例會產生 C3445。  
  
```cpp  
// C3445.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of 
                      //     'A' cannot use an explicit constructor
}
```  
  
若要更正錯誤，請改用直接初始化：  
  
```cpp  
// C3445b.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1{ 1 };
}  
```  
  

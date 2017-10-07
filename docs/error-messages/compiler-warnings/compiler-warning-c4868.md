---
title: "編譯器警告 C4868 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 26031e1ac6f39d745a772e1becf3f817213a59d8
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4868"></a>編譯器警告 C4868
'file(line_number)' 編譯器不會強制執行以括號初始設定式清單由左到右評估順序  
  
 括號初始設定式清單的項目是依照左到右的順序進行評估。 有兩個一些情況下，編譯器無法保證此順序︰ 第一個是當某些項目是以傳值; 的物件第二個是以編譯時`/clr`和某些項目欄位的物件或陣列元素。 當編譯器無法保證左到右評估它就會發出警告 C4868。  
  
 Visual c + + 2015 Update 2 所完成之編譯器一致性處理，可以產生這個警告。 在 Visual c + + 2015 Update 2 之前編譯的程式碼現在會產生 C4868。  
  
 此警告預設為關閉。 使用`/Wall`啟用這項警告。  
  
 若要解決這個警告，請先考慮初始設定式清單項目左到右評估是否有需要，例如當項目評估可能會產生順序而定的副作用。 在許多情況下，項目都計算的順序並沒有顯著的影響。  
  
 如果評估的順序必須是由左到右，請考慮是否可以將項目傳遞 （常數） 的參考。 這類變更可排除下列程式碼範例中的警告。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4868。  
  
```  
// C4868.cpp  
// compile with: /c /Wall  
#include <cstdio>  
  
class HasCopyConstructor  
{  
public:  
    int x;  
  
    HasCopyConstructor(int x): x(x) {}  
  
    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)  
    {  
        printf("Constructing %d\n", h.x);  
    }  
};  
  
class TripWarning4868  
{  
public:  
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.  
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}  
  
    // This variation will not trigger the warning:  
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}  
};  
  
int main()  
{  
    HasCopyConstructor a{1};  
    HasCopyConstructor b{2};  
  
    // the warning will indicate the below line, the usage of the braced initializer list.  
    TripWarning4868 warningOnThisLine{a, b};  
};  
```

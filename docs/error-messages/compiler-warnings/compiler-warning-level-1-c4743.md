---
title: "編譯器警告 (層級 1) C4743 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4743
dev_langs:
- C++
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a7169afdf7fb4c9a03e509f0332e738a66a06f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4743"></a>編譯器警告 (層級 1) C4743
'*類型*'有不同的大小'*file1*'和'*file2*':*數目*和*數目*位元組  
  
 外部變數定義在兩個檔案或參考這些檔案，具有不同類型，編譯器判斷出中變數的大小*file1*中變數的大小與*file2*.  
  
 時，重要的情況下可以用於 c + + 發出這個警告。 如果您宣告相同的型別具有相同名稱在兩個不同的檔案，如果這些宣告包含虛擬函式，而且如果宣告並不相同時，編譯器可發出警告 C4744 虛擬函式的資料表。 針對相同的類型，兩個不同大小的虛擬函式資料表，而連結器必須選擇其中一個，將合併到可執行檔，就會發生警告。  所以這會導致您的程式錯誤的虛擬函式的呼叫。  
  
 若要解決這個警告，請使用相同的類型定義，或使用不同的類型或變數的名稱。  
  
## <a name="example"></a>範例  
 此範例包含一個類型的定義。  
  
```  
// C4743a.cpp  
// compile with: /c  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
};  
  
void C::f1(void) {}  
void C::f2(void) {}  
void C::f3(void) {}  
C q;  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C4743。  
  
```  
// C4743b.cpp  
// compile with: C4743a.cpp /W1 /GL /O2  
// C4743 expected  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
    virtual void f4(void);  
    virtual void f5(void);  
};  
  
void C::f4(void) {}  
void C::f5(void) {}  
C x;  
  
int main() {}   
```
---
title: "編譯器警告 (層級 1) C4743 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4743"
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'*type*' 在 '*file1*' 和 '*file2*' 中有不同的大小：*number* 和 *number* 位元組  
  
 在兩個檔案中已參考或已定義的外部變數各有不同的型別，而編譯器也已判斷 *file1* 中的變數大小與 *file2* 中的變數大小不同。  
  
 在重要的情況下，會為 C\+\+ 發出這項警告。  如果在兩個不同的檔案中，用相同的名稱宣告相同的型別，如果這些宣告包含虛擬函式，而且如果宣告不相同，則編譯器可以為虛擬函式表 \(Virtual Function Table\) 發出 C4744 警告。  因為相同的型別而有兩個不同大小的虛擬函式表，所以發生警告，而連結器必須選擇其中一 個，以納入可執行檔中。這項作業很可能會讓您的程式呼叫不正確的虛擬函式。  
  
 若要解除這項警告，請使用相同的型別定義，或使用該型別或變數的不同名稱。  
  
## 範例  
 這個範例包含一個型別的定義。  
  
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
  
## 範例  
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
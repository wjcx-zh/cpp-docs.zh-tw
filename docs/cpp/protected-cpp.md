---
title: "受保護 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02366a53f02142f66aa5dca493c5460c9f2d1d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>語法  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>備註  
 `protected`關鍵字會指定在類別成員的存取權*成員清單*到下一個存取規範 (**公用**或`private`) 或類別定義結尾。 宣告為 `protected` 的類別成員只能用於下列各項：  
  
-   原本宣告這些成員之類別的成員函式。  
  
-   原本宣告這些成員之類別的 Friend。  
  
-   從原本宣告這些成員的類別中所衍生，具有 public 或 protected 存取權限的類別。  
  
-   直接以 private 方式衍生的類別，這些類別也具有對 protected 成員的 private 存取權限。  
  
 `protected` 關鍵字加在基底類別的名稱前面時，會將基底類別的 public 和 protected 成員指定為其衍生類別的 protected 成員。  
  
 受保護的成員是不一樣為私用`private`成員，只有其宣告，但這些不是做為公用類別的成員才能存取**公用**會員，也就是在任何函式中存取。  
  
 受保護的成員也宣告為**靜態**可存取衍生任何的類別 friend 或成員函式。 受保護的成員不是宣告為**靜態**friend 和成員函式只能透過指標、 參考或衍生類別的物件在衍生類別中存取。  
  
 如需相關資訊，請參閱[friend](../cpp/friend-cpp.md)，[公用](../cpp/public-cpp.md)，[私人](../cpp/private-cpp.md)，和中的成員存取表[控制對類別成員存取](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 專屬資訊  
 在 CLR 類型中，c + + 存取規範關鍵字 (**公用**， `private`，和`protected`) 可能會影響的可見性的型別和組件方面的方法。 如需詳細資訊，請參閱[成員存取控制](member-access-control-cpp.md)。  
  
> [!NOTE]
>  與已編譯的檔案[/LN](../build/reference/ln-create-msil-module.md)不會受到這個行為。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。  
  
## <a name="end-clr-specific"></a>/clr 專屬資訊結束  
  
## <a name="example"></a>範例  
  
```  
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [控制對類別成員存取](member-access-control-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)
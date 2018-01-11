---
title: "public （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: public_cpp
dev_langs: C++
helpviewer_keywords: public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ff41d2b12f43deabd82538a3e2fb10eb35ead16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="public-c"></a>public (C++)
## <a name="syntax"></a>語法  
  
```  
public:  
   [member-list]  
public base-class  
```  
  
## <a name="remarks"></a>備註  
 加類別成員清單前面時**公用**關鍵字可讓您指定的那些成員都可以存取從任何函式。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。  
  
 當基底類別的名稱前面**公用**關鍵字指定基底類別的 public 和 protected 成員是公用和 protected 成員分別衍生類別。  
  
 類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。  
  
 對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。  
  
 如需詳細資訊，請參閱[私人](../cpp/private-cpp.md)，[保護](../cpp/protected-cpp.md)， [friend](../cpp/friend-cpp.md)，和中的成員存取表[控制對類別成員存取](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 專屬資訊  
 在 CLR 類型中，c + + 存取規範關鍵字 (**公用**， `private`，和`protected`) 可能會影響的可見性的型別和組件方面的方法。 如需詳細資訊，請參閱[成員存取控制](member-access-control-cpp.md)。  
  
> [!NOTE]
>  與已編譯的檔案[/LN](../build/reference/ln-create-msil-module.md)不會受到這個行為。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。  
  
## <a name="end-clr-specific"></a>/clr 專屬資訊結束  
  
## <a name="example"></a>範例  
  
```  
// keyword_public.cpp  
class BaseClass {  
public:  
   int pubFunc() { return 0; }  
};  
  
class DerivedClass : public BaseClass {};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   aBase.pubFunc();       // pubFunc() is accessible   
                          //    from any function  
   aDerived.pubFunc();    // pubFunc() is still public in   
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [控制對類別成員存取](member-access-control-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)
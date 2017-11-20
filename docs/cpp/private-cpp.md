---
title: "私用 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: private_cpp
dev_langs: C++
helpviewer_keywords: private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4f6a60a1e152d211ea3894d6dcd221ab543d3997
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="private-c"></a>private (C++)
## <a name="syntax"></a>語法  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## <a name="remarks"></a>備註  
 `private` 關鍵字加在類別成員清單前面時，會指定只能從成員函式和類別的 friend 存取這些成員。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。  
  
 `private` 關鍵字加在基底類別的名稱前面時，會將基底類別的 public 和 protected 成員指定為衍生類別的 private 成員。  
  
 類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。  
  
 對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。  
  
 如需相關資訊，請參閱[friend](../cpp/friend-cpp.md)，[公用](../cpp/public-cpp.md)，[保護](../cpp/protected-cpp.md)，和中的成員存取表[控制存取類別成員](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 專屬資訊  
 在 CLR 類型中，c + + 存取規範關鍵字 (**公用**， `private`，和`protected`) 可能會影響的可見性的型別和組件方面的方法。 如需詳細資訊，請參閱[成員存取控制](member-access-control-cpp.md)。  
  
> [!NOTE]
>  與已編譯的檔案[/LN](../build/reference/ln-create-msil-module.md)不會受到這個行為。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。  
  
## <a name="end-clr-specific"></a>/clr 專屬資訊結束  
  
## <a name="example"></a>範例  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [控制對類別成員存取](member-access-control-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)
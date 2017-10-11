---
title: "static_cast 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- static_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0c8d041ff7b615e4fd8b6e0e54365e92aca2ebc9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="staticcast-operator"></a>static_cast 運算子
將轉換*運算式*的型別*類型 id*只根據出現在運算式中的類型。  
  
## <a name="syntax"></a>語法  
  
```  
static_cast <type-id> ( expression )   
```  
  
## <a name="remarks"></a>備註  
 標準 C++ 不會利用執行階段類型檢查來確認轉換是否安全。 在 C++/CX 中會執行編譯時期和執行階段檢查。 如需詳細資訊，請參閱[轉型](casting.md)。  
  
 `static_cast` 運算子可用於將基底類別指標轉換為衍生類別指標的作業。 這類轉換不一定一直都是安全的。  
  
 一般而言，要將列舉之類的數值資料類型轉換為 int，或將 int 轉換為浮點數，且您確定轉換中的資料類型時，可以使用 `static_cast`。 `static_cast` 轉換的安全性不如 `dynamic_cast` 轉換，因為 `static_cast` 不會進行執行階段類型檢查，但 `dynamic_cast` 會。 模稜兩可指標的 `dynamic_cast` 會失效，而 `static_cast` 則會傳回而看似沒有任何錯誤；這種情況可能會有危險。 雖然 `dynamic_cast` 轉換的安全性較高，但 `dynamic_cast` 只適用於指標或參考，執行階段類型檢查則是額外負荷。 如需詳細資訊，請參閱[dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)。  
  
 在下列範例中，`D* pd2 = static_cast<D*>(pb);` 這一行並不安全，因為 `D` 可能會包含不在 `B` 中的欄位和方法。 不過，`B* pb2 = static_cast<B*>(pd);` 這一行是安全的轉換，因為 `D` 一律都會包含所有的 `B`。  
  
```  
// static_cast_Operator.cpp  
// compile with: /LD  
class B {};  
  
class D : public B {};  
  
void f(B* pb, D* pd) {  
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields  
                                   // and methods that are not in B.  
  
   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always  
                                   // contains all of B.  
}  
```  
  
 相對於[dynamic_cast](../cpp/dynamic-cast-operator.md)，任何執行階段檢查對`static_cast`轉換`pb`。 `pb` 所指向的物件可能不是 `D` 類型的物件，在此情況下，使用 `*pd2` 可能會得不償失。 例如，呼叫屬於 `D` 類別但不屬於 `B` 類別的成員函式時，可能會造成存取違規。  
  
 `dynamic_cast` 和 `static_cast` 運算子會在整個類別階層中移動指標。 不過，`static_cast` 完全依賴 cast 陳述式所提供的資訊，因此可能不安全。 例如：  
  
```  
// static_cast_Operator_2.cpp  
// compile with: /LD /GR  
class B {  
public:  
   virtual void Test(){}  
};  
class D : public B {};  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  
   D* pd2 = static_cast<D*>(pb);  
}  
```  
  
 如果 `pb` 真的指向 `D` 類型的物件，則 `pd1` 和 `pd2` 會取得相同的值。 如果 `pb == 0`，它們也會得到相同的值。  
  
 如果 `pb` 指向 `B` 類型的物件而非完整的 `D` 類別，則 `dynamic_cast` 會知道要傳回零。 不過，`static_cast` 依賴程式設計人員的判斷提示，也就是 `pb` 會指向 `D` 類型的物件，因此只會傳回該假設性 `D` 物件的指標。  
  
 所以，`static_cast` 可以進行反向隱含轉換，而其結果會是未定義。 程式設計人員必須確認 `static_cast` 轉換的結果是否安全。  
  
 此行為也適用於類別類型以外的類型。 例如，您可以使用 `static_cast` 將 int 轉換為 `char`。 不過，產生的 `char` 的位元可能不足以表示整個 `int` 值。 同樣地，它就可讓您確認程式設計人員的結果`static_cast`是安全的轉換。  
  
 `static_cast` 運算子也可用於執行所有隱含轉換，包括標準轉換和使用者定義的轉換。 例如：  
  
```  
// static_cast_Operator_3.cpp  
// compile with: /LD /GR  
typedef unsigned char BYTE;  
  
void f() {  
   char ch;  
   int i = 65;  
   float f = 2.5;  
   double dbl;  
  
   ch = static_cast<char>(i);   // int to char  
   dbl = static_cast<double>(f);   // float to double  
   i = static_cast<BYTE>(ch);  
}  
```  
  
 `static_cast` 運算子可以將整數值明確轉換為列舉類型。 如果整數類型的值不在列舉值的範圍內，所產生的列舉值就是未定義的值。  
  
 `static_cast` 運算子會將 null 指標值轉換為目的類型的 null 指標值。  
  
 `static_cast` 運算子可以將所有運算式明確轉換為 void 類型。 目的 void 類型可以選擇性地包含 `const`、`volatile` 或 `__unaligned` 屬性。  
  
 `static_cast` 運算子不能沒有 `const`、`volatile` 或 `__unaligned` 屬性。 請參閱[const_cast 運算子](../cpp/const-cast-operator.md)如需移除這些屬性的資訊。  
  
 由於在重新配置的記憶體回收行程之上執行未檢查的轉換並不安全，因此，除非您確定在效能嚴重不足的程式碼中可以正確執行，否則請勿使用 `static_cast`。 如果您必須使用`static_cast`在發行模式中取代[safe_cast](../windows/safe-cast-cpp-component-extensions.md)在偵錯組建中，以確保成功。  
  
## <a name="see-also"></a>另請參閱  
 [轉型運算子](../cpp/casting-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)

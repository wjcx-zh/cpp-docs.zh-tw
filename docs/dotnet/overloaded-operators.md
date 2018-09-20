---
title: 多載運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operator overloading, in a CLR class
- operators [C++], overloading
ms.assetid: 30391426-afe7-4497-bf22-e4816c1e48c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a53b8df6f10a4fb8efcd91ce5d9c3f0125320139
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425856"
---
# <a name="overloaded-operators"></a>多載運算子

運算子多載已大幅改變 Managed Extensions for c + + Visual c + +。

在宣告中的參考型別，如範例中，而不是使用原生`operator+`語法中，您明確地寫出的運算子為基礎的內部名稱在此情況下， `op_Addition`。 此外，運算子的引動過程就必須明確地叫用透過該名稱，因此抹煞運算子多載兩個主要優點: （a） 以直覺的語法，以及與現有類型的新型別混合 （b） 的能力。 例如: 

```
public __gc __sealed class Vector {
public:
   Vector( double x, double y, double z );

   static bool    op_Equality( const Vector*, const Vector* );
   static Vector* op_Division( const Vector*, double );
   static Vector* op_Addition( const Vector*, const Vector* );
   static Vector* op_Subtraction( const Vector*, const Vector* );
};

int main()
{
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );

   Vector *pc1 = Vector::op_Addition( pa, pb );
   Vector *pc2 = Vector::op_Subtraction( pa, pc1 );
   Vector *pc3 = Vector::op_Division( pc1, pc2->x );

   if ( Vector::op_Equality( pc1, pc2 ))
      ;
}
```

在新語法中，會還原一般原生的 c + + 程式設計人員的期望，宣告和使用靜態運算子中所示。 以下是`Vector`類別轉譯成新的語法：

```
public ref class Vector sealed {
public:
   Vector( double x, double y, double z );

   static bool    operator ==( const Vector^, const Vector^ );
   static Vector^ operator /( const Vector^, double );
   static Vector^ operator +( const Vector^, const Vector^ );
   static Vector^ operator -( const Vector^, const Vector^ );
};

int main()
{
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );
   Vector^ pb = gcnew Vector( 1.475,4.8916,-1.23 );

   Vector^ pc1 = pa + pb;
   Vector^ pc2 = pa - pc1;
   Vector^ pc3 = pc1 / pc2->x;

   if ( pc1 == pc2 )
      ;
}
```

## <a name="see-also"></a>另請參閱

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
---
title: 屬性索引宣告 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6917742b285b3700548b54fef164d01c0594e5e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380461"
---
# <a name="property-index-declaration"></a>屬性索引宣告

宣告的索引的屬性的語法已從 Managed Extensions for c + + Visual c + +。

索引屬性的 Managed Extensions 的語言支援的兩個主要的缺點是無法提供類別層級註標;也就是說，所有索引的屬性所指定的名稱，而因此沒有任何方法，例如，提供可直接套用至受管理的註標運算子`Vector`或`Matrix`類別物件。 第二個小缺點是，以視覺化方式難以區分屬性與索引屬性-參數的數目是唯一的指示。 最後，索引的屬性會發生相同問題的非索引屬性-存取子不視為不可部分完成的單位，但分成個別的方法。  例如: 

```
public __gc class Vector;
public __gc class Matrix {
   float mat[,];

public:
   __property void set_Item( int r, int c, float value);
   __property float get_Item( int r, int c );

   __property void set_Row( int r, Vector* value );
   __property Vector* get_Row( int r );
};
```

您可以在這裡看到，索引子的區別僅在於額外的參數來指定兩個或單一維度的索引。 在新語法中，索引子的括號 （[、]） 的索引子名稱後面，並指出每個索引的類型與數量來區別：

```
public ref class Vector {};
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   property float Item [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

若要表示可以直接套用到在新語法中，類別的物件類別層級索引子`default`關鍵字會重複使用來取代明確的名稱。 例如: 

```
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   // ok: class level indexer now
   //
   //     Matrix mat;
   //     mat[ 0, 0 ] = 1;
   //
   // invokes the set accessor of the default indexer

   property float default [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

在新語法中，預設值建立索引時會屬性已指定，會保留兩個下列名稱：`get_Item`和`set_Item`。 這是因為這些是基礎產生預設索引屬性的名稱。

請注意，有沒有簡單的索引的語法類似於簡單的屬性語法。

## <a name="see-also"></a>另請參閱

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)

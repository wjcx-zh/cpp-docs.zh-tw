---
title: 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 019b8eae17952bfe53fd8fbf14db4bafce1bf463
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438297"
---
# <a name="property-declaration"></a>屬性宣告

宣告 managed 類別中的屬性的方式已經從 Managed Extensions for c + + Visual c + +。

Managed Extensions 中設計，每個`set`或`get`屬性存取子會指定為獨立的方法。 每個方法的宣告前面會加上`__property`關鍵字。 方法名稱的開頭是`set_`或`get_`後面接著 （以向使用者顯示） 之屬性的實際名稱。 因此，`Vector`提供`x`協調`get`屬性會將它命名`get_x`使用者會叫用它做為`x`。 此命名慣例和方法的個別規格實際上是代表基礎執行階段實作的屬性。 例如，以下是我們`Vector`與一組座標的屬性：

```
public __gc __sealed class Vector {
public:
   __property double get_x(){ return _x; }
   __property double get_y(){ return _y; }
   __property double get_z(){ return _z; }

   __property void set_x( double newx ){ _x = newx; }
   __property void set_y( double newy ){ _y = newy; }
   __property void set_z( double newz ){ _z = newz; }
};
```

這分散屬性相關聯的功能，並要求使用者在語彙上整合的相關聯的設定和取得。 此外，它是詳細資訊。 在新語法中，也就是比較類似 C#，`property`關鍵字後面的屬性和它的未裝飾的名稱的類型。 `set`和`get`存取方法都位於區塊的屬性名稱後面。 請注意，不同於 C# 中，會指定存取方法的簽章。 例如，以下是上述程式碼範例轉譯成新的語法。

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

      void set( double newx ) {
         _x = newx;
      }
   } // Note: no semi-colon
};
```

如果屬性的存取方法可例如反映不同的存取層級-`public get`和`private`或`protected set`，您可以指定明確的存取標籤。 根據預設，屬性的存取層級會反映出的封入的存取層級。 例如，在上述的定義`Vector`，這兩個`get`並`set`方法都是`public`。 若要讓`set`方法`protected`或`private`，定義會修改，如下所示：

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

   private:
      void set( double newx ) {
         _x = newx;
      }

   } // note: extent of private culminates here

// note: dot is a public method of Vector
double dot( const Vector^ wv );

// etc.
};
```

存取關鍵字屬性內的範圍會延伸至任一個右大括號的屬性或其他存取關鍵字的規格。 它不會延伸超過為封閉在其中定義該屬性的存取層級屬性的定義。 在上述宣告中，例如`Vector::dot()`是公用的方法。

寫入設定/取得屬性的三個`Vector`座標包含三個步驟：

1. 宣告私用狀態的成員適當的型別。

1. 當使用者想要取得其值將它傳回。

1. 將它指派新值。

在新語法中的縮寫屬性語法可會自動化這種使用模式：

```
public ref class Vector sealed {
public:
   // equivalent shorthand property syntax
   property double x;
   property double y;
   property double z;
};
```

速記屬性語法的有趣的副作用是，雖然 backstage 狀態成員由編譯器所產生的但它不能存取以外的類別，透過設定/取得存取子內。

## <a name="see-also"></a>另請參閱

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[屬性](../windows/property-cpp-component-extensions.md)
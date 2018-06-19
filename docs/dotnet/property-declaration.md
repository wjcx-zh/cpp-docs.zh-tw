---
title: 屬性宣告 |Microsoft 文件
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
ms.openlocfilehash: bc2cf76384078e579756abe653fb45fd1e97707f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161573"
---
# <a name="property-declaration"></a>屬性宣告
宣告 managed 類別中的屬性的方法已從 Managed Extensions for c + + Visual c + +。  
  
 在 Managed Extensions 設計，每個`set`或`get`屬性存取子會指定為獨立的方法。 每個方法的宣告前面會加上`__property`關鍵字。 方法名稱的開頭是`set_`或`get_`後面 （當做使用者可以看見） 之屬性的實際名稱。 因此，`Vector`提供`x`協調`get`屬性會將其命名`get_x`和使用者會叫用它做為`x`。 這個命名慣例及方法的個別規格實際上會反映基礎執行階段實作的屬性。 例如，以下是我們`Vector`與一組座標的屬性：  
  
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
  
 這與屬性相關聯的功能會散佈，並要求使用者在語彙上進行整合的相關聯的集和取得。 此外，它會詳細資訊。 在新的語法中，則更像 C#，`property`關鍵字後面的屬性和其原始的名稱的類型。 `set`和`get`存取方法都放置在區塊的屬性名稱後面。 請注意不同於 C# 中，會指定存取方法的簽章。 例如，以下是上述程式碼範例轉譯成新的語法。  
  
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
  
 如果屬性存取方法可如反映不同的存取層級-`public get`和`private`或`protected set`，您可以指定之明確存取標籤。 根據預設，屬性的存取層級會反映封入的存取層級。 例如，在上述的定義`Vector`，這兩個`get`和`set`方法`public`。 若要讓`set`方法`protected`或`private`，會修改定義如下：  
  
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
  
 存取關鍵字在屬性中的範圍會延伸至屬性的任一個的右括號或其他存取關鍵字的規格。 它不會延伸超過要在其中定義屬性的封入的存取層級之屬性的定義。 在上述宣告中，例如`Vector::dot()`是公用的方法。  
  
 將三種 set/get 屬性`Vector`座標和三個步驟：  
  
1.  宣告私用狀態的適當類型的成員。  
  
2.  當使用者想要取得其值將它傳回。  
  
3.  指派新值。  
  
 在新語法中的縮寫屬性語法是使用會自動化此使用方式模式：  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 速記屬性語法的有趣的副作用是，雖然幕後狀態成員會由編譯器所產生，但它不能存取在類別內除非透過 set/get 存取子。  
  
## <a name="see-also"></a>另請參閱  
 [在類別或介面中的成員宣告 (C + + /CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [屬性](../windows/property-cpp-component-extensions.md)
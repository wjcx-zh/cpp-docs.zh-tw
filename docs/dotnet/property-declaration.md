---
title: "屬性宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property 關鍵字"
  - "宣告屬性類別, C++"
  - "property 關鍵字 [C++]"
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 屬性宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，在 Managed 類別中宣告屬性的方式已變更。  
  
 在 Managed Extensions 設計中，每個 `set` 或 `get` 屬性存取子都指定為獨立方法。  每個方法的宣告都會以 `__property` 關鍵字做為前置字元。  方法名稱會以 `set_` 或 `get_` 為開頭，後面接著屬性的實際名稱 \(就像使用者所見到的\)。  因此，提供 `x` 座標 `get` 屬性的 `Vector` 將會把它命名為 `get_x`，而使用者會將它叫用為 `x`。  方法的這個命名慣例及個別規格真實地反映屬性的基礎執行階段實作。  例如，這裡是擁有座標屬性集的 `Vector`：  
  
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
  
 這會擴大與屬性相關聯的功能，而且要求使用者必須在語彙上統一相關聯的 set 和 get。  此外，它並不簡潔。  新語法與 C\# 的語法較為相似，它的 `property` 關鍵字後面會接著屬性類型和未經修飾的名稱。  `set` 和 `get` 存取方法是放置在屬性名稱後面的區塊內。  請注意，不同於 C\#，新的語法會指定存取方法的簽章 \(Signature\)。  例如，下列提供上述轉譯成新語法的程式碼範例。  
  
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
  
 如果屬性的存取方法反映不同的存取層級 \(例如，`public` `get` 和 `private` 或 `protected` `set`\)，則可以指定明確的存取標籤。  根據預設，屬性的存取層級會反映封入存取層級的存取層級。  例如，在上述的 `Vector` 定義中，`get` 和 `set` 方法都是 `public`。  若要讓 `set` 方法成為 `protected` 或 `private`，則定義應修改為：  
  
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
  
   } // note: extent of private culminates here …  
  
// note: dot is a public method of Vector  
double dot( const Vector^ wv );  
  
// etc.  
};  
```  
  
 屬性中的存取關鍵字範圍，會延伸至屬性的右邊大括號或其他存取關鍵字的規格。  它不會延伸超出屬性的定義，藉以封入已定義之屬性的存取層級。  例如，在上述宣告中，`Vector::dot()` 是公用方法。  
  
 為這三個 `Vector` 座標撰寫 set\/get 屬性有三個步驟：  
  
1.  宣告適當型別的私用狀態成員。  
  
2.  在使用者希望取得它的值時將它傳回。  
  
3.  為它指派新值。  
  
 在新語法中，可以使用會自動化此使用模式的縮寫屬性語法：  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 縮寫屬性語法有個有趣的副作用，那就是雖然編譯器會產生幕後狀態成員，但在類別內除非透過 set\/get 存取子否則無法存取。  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [property](../windows/property-cpp-component-extensions.md)
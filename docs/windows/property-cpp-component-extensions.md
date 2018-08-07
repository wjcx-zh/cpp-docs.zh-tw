---
title: 屬性 （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fbf0b3c9db19e839d6832415cfd8ed6eb9b93a2
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604114"
---
# <a name="property--c-component-extensions"></a>property (C++ 元件擴充功能)
宣告*屬性*，這是成員函式的行為模式，以及存取資料成員或陣列元素。  
  
## <a name="all-runtimes"></a>所有執行階段  
 您可以宣告下列其中一個類型的屬性。  
  
 *簡單屬性*  
 根據預設，會建立*set 存取子*，將屬性的值，指派*get 存取子*，它會擷取屬性值，以及編譯器所產生的私用資料成員包含屬性值。  
  
 *屬性區塊*  
 使用此選項可建立使用者定義的 get 和/或 set 存取子。 如果同時定義了 get 和 set 存取子，屬性為讀取/寫入；如果只定義 get 存取子，屬性為唯讀，而如果只定義 set 存取子，屬性為唯寫。  
  
 您必須明確宣告資料成員，才能包含屬性值。  
  
 *索引的屬性*  
 您可以用來取得和設定由一個或多個索引所指定之屬性值的屬性區塊。  
  
 您可以建立索引的屬性具有使用者定義的屬性名稱或*預設*屬性名稱。 預設索引屬性的名稱是定義屬性所在的類別的名稱。 若要宣告預設屬性，指定**預設**關鍵字，而不是屬性名稱。  
  
 您必須明確宣告資料成員，才能包含屬性值。 針對索引的屬性，資料成員通常是陣列或集合。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property type property_name;

property type property_name { 
   access-modifier type get() inheritance-modifier {property_body}; 
   access-modifier void set(type value) inheritance-modifier {property_body};
} 

property type property_name[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body}; 
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
} 

property type default[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}  
```  
  
### <a name="parameters"></a>參數  
 *type*  
 屬性值的資料類型，所以是屬性本身。  
  
 *property_name*  
 屬性的名稱。  
  
 *存取修飾詞*  
 存取限定詞。 有效的限定詞都**靜態**並**虛擬**。  
  
 Get 或 set 存取子不需要同意**虛擬**，但是它們必須同意**靜態**限定詞。  
  
 *繼承修飾詞*  
 繼承限定詞。 有效的限定詞都**抽象**並**密封**。  
  
 *index_list*  
 一或多個索引的逗號分隔清單。 每個索引的組成為索引類型以及可在屬性方法主體中使用的選擇性識別碼。  
  
 *值*  
 要指派給 set 作業或在 get 作業中擷取的屬性的值。  
  
 *property_body*  
 set 或 get 存取子的屬性方法主體。 *Property_body*可用*index_list*存取基礎屬性資料成員，或使用者定義的處理中的參數。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 如需詳細資訊，請參閱 <<c0> [ 屬性 (C + + /CX)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx)。  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
### <a name="syntax"></a>語法  
  
```cpp  
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}  
```  
  
### <a name="parameters"></a>參數  
  
 *修飾詞*  
 可以在屬性宣告或 get/set 存取子方法上使用修飾詞。 可能的值為**靜態**並**虛擬**。  
  
 *type*  
 屬性表示之值的類型。  
  
 *property_name*  
 raise 方法的參數；必須符合委派的簽章。  
  
 *index_list*  
 一個或多個索引的逗號分隔清單，在方括號(下標運算子 []) 內指定。 針對每個索引，指定類型以及可以用在屬性方法主體中的選擇性識別碼。  
  
### <a name="remarks"></a>備註  
  
 第一個語法範例會示範*簡單的屬性*，其中隱含宣告同時`set`和`get`方法。 編譯器會自動建立私用欄位來儲存屬性的值。  
  
 第二個語法範例會示範*屬性區塊*，其中明確宣告同時`set`和`get`方法。  
  
 第三個語法範例會顯示客戶定義*index 屬性*。 索引屬性除了要設定或擷取的值以外，還會接受參數。 您必須指定屬性的名稱。 與簡單屬性不同的是，索引屬性的 `set` 和/或 `get` 方法必須明確定義，而且您必須指定屬性的名稱。  
  
 第四個語法範例會示範*預設*屬性，提供類似陣列的存取權類型的執行個體。 關鍵字**預設**，只用來指定預設屬性。 預設屬性的名稱是定義屬性所在的類型的名稱。  
  
 **屬性**關鍵字可以出現在類別、 介面或實值型別。 屬性可以有 get 函式 (唯讀)、set 函式 (唯寫)，或兩者皆有 (可讀寫)。  
  
 屬性名稱不可與包含該屬性之 Managed 類別的名稱相符。 getter 函式的傳回型別必須符合對應 setter 函式之最後一個參數的類型。  
  
 對用戶端程式碼來說，屬性具有一般資料成員的外觀，並且可使用與資料成員相同的語法往返寫入或讀取。  
  
 Get 和 set 方法不需要同意**虛擬**修飾詞。  
  
 get 和 set 方法的可及性可能不同。  
  
 屬性方法的定義可能出現在類別主體外，如同一般的方法。  
  
 Get 和屬性的 set 方法應該同意**靜態**修飾詞。  
  
 如果屬性的 get 和 set 方法符合下列描述，則屬性為純量：  
  
-   get 方法沒有參數，且有傳回類型 `T`。  
  
-   Set 方法具有參數的型別`T`，並傳回型別**void**。  
  
 具有相同識別項的範圍內應該只宣告一個純量屬性。 純量屬性不可多載。  
  
 宣告屬性資料成員時，編譯器會在類別中插入資料成員 — 有時稱為「備份存放區」。 不過，資料成員名稱是一種您不能在來源中參考成員的形式，如同它是包含類別的實際資料成員。 使用 ildasm.exe 來檢視您類型的中繼資料，並查看屬性的備份存放區編譯器產生的名稱。  
  
 屬性區塊中的存取子方法允許不同的可及性。  也就是說，set 方法可以是公用，而 get 方法可以是私人。  不過，存取子方法的可及性較屬性本身上所宣告的更不受限制是一種錯誤。  
  
 **屬性**是內容相關性關鍵字。  如需詳細資訊，請參閱 <<c0> [ 即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/clr`  
  
### <a name="examples"></a>範例  
 下列範例顯示屬性資料成員和屬性區塊的宣告和使用。  它也會顯示可以從類別定義的屬性存取子。  
  
```cpp  
// mcppv2_property.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   int MyInt;  
public:  
  
   // property data member  
   property String ^ Simple_Property;  
  
   // property block  
   property int Property_Block {  
  
      int get();  
  
      void set(int value) {  
         MyInt = value;  
      }  
   }  
};  
  
int C::Property_Block::get() {  
   return MyInt;  
}  
  
int main() {  
   C ^ MyC = gcnew C();  
   MyC->Simple_Property = "test";  
   Console::WriteLine(MyC->Simple_Property);  
  
   MyC->Property_Block = 21;  
   Console::WriteLine(MyC->Property_Block);  
}  
```  
  
 **輸出**  
  
```Output  
test  
  
21  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)
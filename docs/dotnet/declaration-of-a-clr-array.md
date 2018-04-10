---
title: CLR 陣列的宣告，|Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3f263227d437ddafb65ac3da0829414e4af05855
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="declaration-of-a-clr-array"></a>CLR 陣列的宣告
宣告的語法，具現化，並初始化 managed 的陣列已從 Managed Extensions for c + + Visual c + +。  
  
 CLR 陣列物件的宣告在 Managed Extensions 是標準陣列宣告中的延伸模組`__gc`關鍵字已放置於陣列物件的名稱和其可能是逗號填入維度，如同下列配對之間範例：  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 在新語法中，我們可以在其中使用的範本類似的宣告類似於 c + + 標準程式庫已經簡化了這`vector`宣告。 第一個參數表示的項目類型。 第二個參數指定的陣列維度 （預設值為 1 時，多個維度，只需要第二個引數）。 陣列物件本身是追蹤控制代碼，所以必須給予也就是 hat。 如果項目型別也是參考類型，也需要 hat。 例如，上述範例中，當新語法中，以表示如下所示：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 參考型別是追蹤控制代碼，而不是物件，因為它是 CLR 陣列指定為函式的傳回型別。 （相反地，它不可能將原生陣列指定為函式的傳回型別。）如此一來受管理的擴充功能中的語法已稍微非直覺式。 例如:   
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 在 Visual c + + 中，宣告會更簡單。 例如，套用至物件的  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 縮寫初始化本機 managed 陣列的支援語言的這兩個版本。 例如:   
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 已大幅簡化在新語法 (請注意，boxing 是隱含在新語法中，因為`__box`因為已消除運算子-請參閱[實值類型和其行為 (C + + CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)討論):  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 陣列是 CLR 參考類型，因為每個陣列物件的宣告是追蹤控制代碼。 因此，必須先在 CLR 堆積配置陣列物件。 （縮寫標記法隱藏 managed 的堆積配置）。以下是管理擴充功能下的陣列物件初始化的明確形式：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 在新語法中，`new`運算式取代`gcnew`。 維度大小會當做參數傳遞給`gcnew`運算式，如下所示：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 在新語法中，可以遵循明確初始設定清單`gcnew`運算式; 這不支援在 Managed Extensions。 例如:   
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="see-also"></a>請參閱  
 [Managed 類型 (C + + CL)](../dotnet/managed-types-cpp-cl.md)   
 [陣列](../windows/arrays-cpp-component-extensions.md)
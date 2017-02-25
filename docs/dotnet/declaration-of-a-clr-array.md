---
title: "CLR 陣列的宣告 | Microsoft Docs"
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
  - "array 關鍵字 [C++]"
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CLR 陣列的宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，宣告、執行個體化和初始化 Managed 陣列的語法都已變更。  
  
 在 Managed Extensions 中，CLR 陣列物件的宣告是標準陣列宣告的擴充，其中 `__gc` 關鍵字會放在陣列物件名稱和可能的逗號填入維度 \(Dimension\) 之間，如下列這組範例所示：  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 這點在新語法中已經簡化，因為我們使用如範本一樣的宣告，類似 STL `vector` 宣告。  第一個參數表示項目型別。  第二個參數會指定陣列維度 \(預設值為 1，因此只有多個維度需要第二個引數\)。  陣列物件本身是追蹤控制代碼，所以必須給予帽型符號。  如果元素型別也是參考型別，就一樣需要帽型符號。  例如，在新語法中會如下所示表示上述範例：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 由於參考型別是追蹤控制代碼而非物件，因此可以將 CLR 陣列指定做為函式的傳回型別 \(相反地，您無法將原生陣列指定做為函式的傳回型別\)。在 Managed Extensions 中，完成這項工作的語法則是稍微非直覺式的。  例如：  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中，宣告簡單得多。  例如：  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 在兩種語言版本中都支援本機 Managed 陣列的簡略初始設定。  例如：  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 在新語法中已經非常簡化 \(請注意，Boxing 在新語法中是隱含的，因此已排除 `__box` 運算子。請參閱[實值類型和行為 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)中的討論\)：  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 由於陣列是 CLR 參考型別，所以每個陣列物件的宣告都是追蹤控制代碼。  因此，陣列物件必須配置於 CLR 堆積 \(Heap\) 上 \(簡略標記法會隱藏 Managed 堆疊配置\)。下列是在 Managed Extensions 中之陣列物件初始化的明確格式：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 在新語法中，`gcnew` 已取代 `new` 運算式。  維度大小會當做參數傳遞至 `gcnew` 運算式，如下所示：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 在新語法中，明確初始化清單可以接在 `gcnew` 運算式之後，但在 Managed Extensions 中則不支援。  例如：  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## 請參閱  
 [Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Arrays](../windows/arrays-cpp-component-extensions.md)
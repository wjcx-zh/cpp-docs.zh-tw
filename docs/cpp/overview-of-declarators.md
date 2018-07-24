---
title: 宣告子概觀 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, about declarators
ms.assetid: 0f2e2312-80bd-4154-8345-718bd9ed2173
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 405ef6da02c15e93e516069c1fedc22f002bdf2c
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208558"
---
# <a name="overview-of-declarators"></a>宣告子概觀
宣告子是用來指定物件或函式名稱的宣告元件。 宣告子也可將具名物件指定為物件、指標、參考或陣列。  當宣告子未指定基底類型時，會將基底類型中的類型資訊修改為指定的衍生類型，如指標、參考和陣列。  套用至函式時，宣告子會搭配類型規範，將函式的傳回類型完整指定為物件、指標或參考。 (規範，所述[宣告和定義](declarations-and-definitions-cpp.md)，傳達等型別和儲存類別屬性。 在本節中，然後在討論的修飾詞[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)，宣告子修改。)下圖顯示 `MyFunction` 的完整宣告，以及呼叫宣告的元件。  
  
 ![修飾詞、 規範和宣告子](../cpp/media/vc38qy1.gif "vc38QY1")  
規範、修飾詞和宣告子  
  
 **Microsoft 專屬**  
  
 大部分的 Microsoft 擴充關鍵字都可做為形成衍生類型的修飾詞使用，不過它們並不是規範或宣告子。 (請參閱[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)。)  
  
 **結束 Microsoft 專屬**  
  
 宣告子在宣告語法中會出現在選用規範清單之後。 中會討論這些規範[宣告。](declarations-and-definitions-cpp.md) 宣告可以包含多個宣告子，不過，每個宣告子只能宣告一個名稱。  
  
 下列範例宣告顯示如何將規範和宣告子合併，以組成完整的宣告：  
  
```cpp 
const char *pch, ch;  
```  
  
 在上述宣告中，關鍵字**const**並**char**組成規範清單。 其中列出兩個宣告子：`*pch` 和 `ch`。  宣告多個實體的宣告包含類型規範，後面接著宣告子的逗號分隔清單，最後以分號結尾。  
  
 **簡單物件的宣告子**  
  
 簡單物件 (如 int 或 double) 的宣告子只需要由其名稱表示，並可選擇是否加上括號。  
  
 `int i; // declarator is i`  
  
 `int (i); // declarator is (i)`  
  
 **指標、 參考和陣列宣告子**  
  
 在名稱前面插入指標運算子會使物件變成指標或參考。  **\*** 運算子宣告為指標的名稱**&** 運算子會將它宣告為參考。  
  
```cpp 
int *i; // declarator is *i  
int **i; // declarator is **i;  
int &i = x; // declaratory is &i  
```  
  
 附加**const**或是**volatile**為指標指定這些特殊屬性。  在宣告子中使用這些規範 (相對於在類型規範中使用) 會修改指標的屬性，而不是修改所指向的物件：  
  
```cpp 
char *const cpc; // const pointer to char   
const char *pcc; // pointer to const char   
const char *const cpcc; // const pointer to const char  
```  
  
 進一步的資訊可能位於[const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)。  
  
 類別或結構成員的指標是使用適當的巢狀命名規範加以宣告：  
  
```cpp 
int X::* pIntMember;   
int ::X::* pIntMember; // the initial :: specifies X is in global scope  
char Outer::Inner::* pIntMember; // pointer to char in a nested class  
```  
  
 在名稱之後將選擇性常數運算式用方括號括住，會使物件變成陣列。  後續括號會宣告陣列的其他維度。  
  
```cpp 
int i[5]; // array with five elements of type int numbered from 0 to 4  
int i[]; // array of unknown size  
char *s[4]; // array of pointers to char  
int i[2][2]; // two dimensional array  
```  
  
 **函式的宣告子**  
  
 內含引數清單的括號是在宣告函式的名稱之後使用。  下列項目宣告的函式的傳回型別**int**和三個引數的型別**int**。  
  
```cpp 
int f(int a, int b, int c);  
```  
  
 函式的指標和參考的宣告方式是在函式名稱的前面加上指標或參考運算子，如下所示。  需要括號 (通常是選擇性的) 來區分函式的指標與傳回指標的函式：  
  
```cpp 
int (*pf)(int); // pointer to function returning int  
int *f(int i); // function returning pointer to int  
int (&pf)(int); // reference to function   
```  
  
 成員函式的指標會使用巢狀命名規範加以區分：  
  
```cpp 
int (X::* pmf)(); // pointer to member function of X returning int  
int* (X::* pmf)(); // pointer to member function returning pointer to int  
```  
  
 另請參閱[成員的指標](../cpp/pointers-to-members.md)。  
  
 **函式和物件相同的宣告中**  
  
 函式和物件可能會在相同宣告中進行宣告，如下所示：  
  
```cpp 
int i, *j, f(int k);  // int, pointer to int, function returning int  
```  
  
 此語法在某些情況下可能會使人產生誤解。  下列宣告  
  
```cpp 
int* i, f(int k);  // pointer to int, function returning int (not int*)  
```  
  
 可能看起來像是宣告**int**指標，函式傳回`int*`，但不是。  這是因為\*是的宣告子的一部分`i`不屬於的宣告子、 `f`。  
  
 **使用 typedef 簡化宣告子語法**  
  
 更好的技術，不過，是使用**typedef**或 括號的組合並**typedef**關鍵字。 考慮為函式宣告指標陣列：  
  
```cpp 
//  Function returning type int that takes one   
//   argument of type char *.  
typedef int (*PIFN)( char * );  
//  Declare an array of 7 pointers to functions   
//   returning int and taking one argument of type   
//   char *.  
PIFN pifnDispatchArray[7];  
```  
  
 相同的宣告可以寫入不含**typedef**宣告，但它是複雜錯誤可能會超過任何權益：  
  
```cpp 
int ( *pifnDispatchArray[7] )( char * );  
```  
  
 如需有關 typedef 的詳細資訊，請參閱[別名和 typedef](aliases-and-typedefs-cpp.md)。  
  
 單一基底類型的指標、參考和陣列可以在單一宣告 (以逗號分隔) 中合併如下  
  
```cpp 
int a, *b, c[5], **d, &e=a;  
```  
  
 **更複雜的宣告子語法**  
  
- 您可以結合指標、參考、陣列和函式宣告子，將這類物件指定為函式的指標陣列和陣列的指標等等。  
  
- 下列遞迴文法完整描述指標宣告子的語法。  
  
- `declarator` 會定義為下列其中一項：  

  - 識別項   
  - 限定名稱   
  - 宣告子 （引數清單） [cv-qualfiers] [例外狀況規格]  
  - 宣告子 [[常數運算式]]
  - 指標運算子的宣告子   
  - （宣告）  

  
- 並*指標運算子*是其中一個：  
  
  - \* [cv 限定詞]  
  - & [cv 限定詞]:: 巢狀名稱規範\*[cv 限定詞]  

  
 由於宣告子可能包含其他宣告子，因此可以使用上述規則建構較複雜的衍生類型 (例如指標的陣列、傳回函式指標陣列的函式)。  若要進行建構的每個步驟，可從表示基底資料類型的識別項，以及使用先前的運算式做為 `declarator`，套用上述語法規則開始。  套用語法規則的順序應該與以英文所述運算式的方式相反。  如果套用*指標運算子*語法規則的陣列或函式的運算式，會使用括號，如果您想要的指標陣列或函式，如在下表中的最後一個資料列所示。  
  
 下列範例顯示建構「10 個類型為 int 指標的陣列指標」。  
  
|動詞化運算式|宣告子|套用的語法規則|  
|-----------------------|----------------|-------------------------|  
||`i`|1|  
|指向|`*i`|5|  
|10 的陣列|`(*i)[10]`|4|  
|指向|`*((*i)[10])`|6，然後 5|  
  
 如果使用多個指標、參考、陣列或函式修飾詞，宣告子可能會變得相當複雜。  本主題[解譯更複雜的宣告子](../c-language/interpreting-more-complex-declarators.md)描述如何讀取更複雜的宣告子語法。  主題是適用於 C 和 c + +，雖然 c + +，隨處\*用來表示的指標，限定的名稱，例如 MyClass::\*可用來指定類別成員的指標。
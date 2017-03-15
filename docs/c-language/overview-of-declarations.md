---
title: "宣告概觀 | Microsoft Docs"
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
  - "宣告, 關於宣告"
  - "類型限定詞"
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 宣告概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「宣告」會指定一組識別項的解譯和屬性。  如果宣告也為以識別項命名的物件或函式保留儲存區，則稱為「定義」。變數、函式和類型的 C 宣告具有下列語法：  
  
## 語法  
 `declaration`:  
 *declaration\-specifiers* *attribute\-seq*opt *init\-declarator\-list*opt**;**  
  
 \/\* *attribute\-seq*opt 是 Microsoft 特定 \*\/  
  
 *declaration\-specifiers*：  
 *storage\-class\-specifier declaration\-specifiers* opt  
  
 *type\-specifier declaration\-specifiers*  opt  
  
 *type\-qualifier declaration\-specifiers*  opt  
  
 *init\-declarator\-list*:  
 *init\-declarator*  
  
 *init\-declarator\-list* , *init\-declarator*  
  
 *init\-declarator*:  
 *宣告子*  
  
 *declarator*  **\=**  *initializer*  
  
> [!NOTE]
>  後續章節將不再重複 `declaration` 的這個語法。  後續章節中的語法通常會以 `declarator` 非終端開頭。  
  
 *init\-declarator\-list* 中的宣告包含所要命名的識別項；*init* 是初始設定式的縮寫。  *init\-declarator\-list* 是以逗號分隔的宣告序列，每個宣告都可以有額外的類型資訊及\/或初始設定式。  `declarator` 包含所要宣告的識別項 \(若有的話\)。  *declaration\-specifiers* 非終端是由一個類型序列和儲存類別規範所組成，這些規範會指出連結、儲存期，以及至少一部分宣告子表示的實體類型。  因此，宣告是由儲存類別規範、類型規範、類型限定詞、宣告子和初始設定式的某種組合所構成。  
  
 宣告可以包含 *attribute\-seq* 中列出的一或數個選擇性屬性；*seq* 是序列的縮寫。  這些 Microsoft 特定屬性可執行各種函式，本手冊中會有詳細的討論。  
  
 在一般格式的變數宣告中，*type\-specifier* 會提供變數的資料類型。  *type\-specifier* 可以是複合式的，例如由 **const** 或 `volatile` 修改類型時。  `declarator` 會為變數命名，可能會修改變數以宣告陣列或指標類型。  例如：  
  
```  
int const *fp;  
```  
  
 宣告名為 `fp` 的變數為無法修改之 \(**const**\) `int` 值的指標。  若要定義宣告中的多個變數，您可以使用多個宣告子，並以逗號分隔。  
  
 一個宣告至少要有一個宣告子，否則其類型規範必須宣告結構標記、等位標記或列舉的成員。  宣告子提供有關識別項的任何其餘資訊。  宣告子是一種識別項，可以用方括號 \(**\[ \]**\)、星號 \(**\***\) 或括號 \( **\( \)** \) 來修改，分別宣告陣列、指標或函式類型。  當您宣告簡單變數 \(例如字元、整數和浮點項目\)，或是簡單變數的結構和等位時，`declarator` 就只是識別項。  如需宣告子的詳細資訊，請參閱[宣告子及變數宣告](../c-language/declarators-and-variable-declarations.md)。  
  
 所有定義都是隱含的宣告，但並非所有宣告都是定義。  例如，以 `extern` 儲存類別規範開頭的變數宣告是要「參考」而不是「定義」宣告。  如果在定義外部變數之前先加以參考，或是從使用外部變數的原始程式檔，將其定義在另一個原始程式檔中，則需要 `extern` 宣告。  儲存體不是藉由「參考」宣告來配置，也不能在宣告中初始化變數。  
  
 變數宣告中需要有儲存類別及\/或類型。  除了 `__declspec` 之外，宣告中只允許一個儲存類別規範，而且並非每個內容中都允許所有儲存類別規範。  `__declspec` 儲存類別可以與其他儲存類別規範搭配使用，而且可以多次使用。  宣告的儲存類別規範會影響如何儲存和初始化所宣告的項目，以及程式的哪些部分可以參考該項目。  
  
 C 中定義的 *storage\-class\-specifier* 終端包含 **auto**、`extern`、**register**、**static** 和 `typedef`。  此外，Microsoft C 包含 *storage\-class\-specifier* 終端 `__declspec`。  所有 *storage\-class\-specifier* 終端 \(`typedef` 和 `__declspec` 除外\) 都會在[儲存類別](../c-language/c-storage-classes.md)中加以討論。  如需 `typedef` 的資訊，請參閱 [Typedef 宣告](../c-language/typedef-declarations.md)。  如需 `__declspec` 的資訊，請參閱[擴充儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)。  
  
 宣告在原始程式中的位置，以及變數是否有其他宣告存在，都是判定變數存留期的重要因素。  重新宣告可以有好幾個，但定義只有一個。  不過，定義可以出現在多個轉譯單位中。  針對具有內部連結的物件，此規則分別適用於各轉譯單位，因為內部連結的物件對轉譯單位而言是唯一的。  針對具有外部連結的物件，此規則適用於整個程式。  如需可見性的詳細資訊，請參閱[存留期、範圍、可見性和連結](../c-language/lifetime-scope-visibility-and-linkage.md)。  
  
 類型規範提供識別項資料類型的一些相關資訊。  預設類型規範為 `int`。  如需詳細資訊，請參閱[類型規範](../c-language/c-type-specifiers.md)。  類型規範也可以定義類型標記、結構和等位元件名稱，以及列舉常數。  如需詳細資訊，請參閱[列舉宣告](../c-language/c-enumeration-declarations.md)、[結構宣告](../c-language/structure-declarations.md)和[等位宣告](../c-language/union-declarations.md)。  
  
 有兩個 *type\-qualifier* 終端：**const** 和 `volatile`。  這些限定詞可指定只有透過左值來存取該類型的物件時，才會相關聯的其他類型屬性。  如需 **const** 和 `volatile` 的詳細資訊，請參閱[類型限定詞](../c-language/type-qualifiers.md)。  如需左值定義的詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。  
  
## 請參閱  
 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)   
 [宣告和類型](../c-language/declarations-and-types.md)   
 [宣告摘要](../c-language/summary-of-declarations.md)
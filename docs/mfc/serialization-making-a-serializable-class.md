---
title: "序列化：建立可序列化的類別 | Microsoft Docs"
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
  - "類別 [C++], 衍生"
  - "CObject 類別, 衍生可序列化的類別"
  - "建構函式 [C++], 不使用引數定義"
  - "DECLARE_SERIAL 巨集"
  - "預設建構函式"
  - "預設值 [C++], 建構函式"
  - "IMPLEMENT_SERIAL 巨集"
  - "沒有預設建構函式"
  - "無引數建構函式"
  - "可序列化的類別"
  - "序列化 [C++], 可序列化的類別"
  - "Serialize 方法, 覆寫"
  - "VERSIONABLE_SCHEMA 巨集"
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 序列化：建立可序列化的類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要求五個主要步驟使類別可序列化。  在下面列出並在下列部分說明：  
  
1.  [從 CObject 衍生您的類別](#_core_deriving_your_class_from_cobject) \(或從衍生自 `CObject` 的一些類別\)。  
  
2.  [覆寫序列化成員函式](#_core_overriding_the_serialize_member_function)。  
  
3.  在 類別宣告的[使用 DECLARE\_SERIAL 巨集](#_core_using_the_declare_serial_macro) 。  
  
4.  [定義不採用任何引數的建構函式](#_core_defining_a_constructor_with_no_arguments)。  
  
5.  為您的類別[使用在實作檔的 IMPLEMENT\_SERIAL 巨集](#_core_using_the_implement_serial_macro_in_the_implementation_file) 。  
  
 如果您直接呼叫 `Serialize` 而非透過 [CArchive](../mfc/reference/carchive-class.md) \>\> 和 \<\<  的運算元，則最後三個步驟不為序列化所需。  
  
##  <a name="_core_deriving_your_class_from_cobject"></a> 從 CObject 衍生您的類別  
 基本序列化通訊協定和功能在 `CObject` 類別中定義。  藉由從 `CObject` 衍生您的類別\(或從衍生自 `CObject` 衍生的類別\)，如下列類別 `CPerson` 的宣告，您可以得到對序列化通訊協定和 `CObject` 的功能的存取權。  
  
##  <a name="_core_overriding_the_serialize_member_function"></a> 覆寫序列化成員函式  
 `Serialize` 成員函式，在 `CObject` 類別中定義，會實際序列化所需的資料來擷取物件的目前狀態。  `Serialize` 函式有一個 `CArchive` 引數用來讀取和寫入物件資料。  [CArchive](../mfc/reference/carchive-class.md) 物件具有一個成員函式，`IsStoring`，表示 `Serialize` 是否儲存\(寫入資料\)或載入\(讀取\)。  使用 `IsStoring` 的結果做為教學課程中，您可以使用插入運算子 \(**\<\<**\) 在 `CArchive` 插入您物件的資料或使用擷取運算子 \(**\>\>**\) 擷取資料。  
  
 請考慮衍生自 `CObject` 並有兩個型別為 `CString` 和 **WORD**的新成員變數的類別。  下列類別宣告片段顯示新成員變數和要覆寫 `Serialize` 成員函式的宣告：  
  
 [!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_1.h)]  
  
#### 若要覆寫序列化成員函式  
  
1.  呼叫您的 `Serialize` 的基底類別版本來確保物件的繼承部分序列化。  
  
2.  插入或擷取您的類別指定的成員變數。  
  
     插入和擷取運算子互動以封存類別來讀取和寫入資料。  下列程式碼範例將示範如何為上面宣告的 `CPerson` 實作 `Serialize` 類別。  
  
     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_2.cpp)]  
  
 您也可以使用 [CArchive::Read](../Topic/CArchive::Read.md) 和 [CArchive::Write](../Topic/CArchive::Write.md) 成員函式來讀取和寫入很多不具型別的資料。  
  
##  <a name="_core_using_the_declare_serial_macro"></a> 使用 DECLARE\_SERIAL 巨集  
 `DECLARE_SERIAL` 巨集為支援序列化類別的宣告所需要，如下所示：  
  
 [!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_3.h)]  
  
##  <a name="_core_defining_a_constructor_with_no_arguments"></a> 定義沒有引數的建構函式  
 當它在還原序列化重新建立您的物件時 \(從磁碟載入\)，MFC 需要預設建構函式。  還原序列化程序需要的值將會填入所有成員變數來重新建立物件。  
  
 這個建構函式可以宣告為公用、保護或私用。  如果您將控制項設定私用或保護，有助於確保它只能由序列化函式使用。  建構函式必須讓物件處於可視需要刪除的狀態。  
  
> [!NOTE]
>  如果在使用 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 巨集的類別忘記定義不搭配引數的建構函式，則會得到「沒有預設建構函式可使用」的編譯警告在使用 `IMPLEMENT_SERIAL` 聚集的那一行。  
  
##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> 在實作檔使用 IMPLEMENT\_SERIAL 巨集  
 當您從 `CObject` 衍生一個可序列化類別時， `IMPLEMENT_SERIAL` 巨集被用來定義需要的各種功能。  您在實作檔 \(.CPP\) 為您的類別使用這個巨集。  對巨集的最前面兩個引數為類別的名稱及其直接基底類別的名稱。  
  
 對這個巨集的第三個引數是結構描述數目。  結構描述數字基本上是類別之物件的版本號碼。  結構描述數字使用大於或等於0的整數。\(請勿將這個結構描述數字混淆資料庫詞彙中\)。  
  
 當物件讀取至記憶體時，MFC 序列化程式碼會檢查結構描述數字。  如果在磁碟上物件的結構描述數字不符合類別在記憶體的結構描述數字，程式庫會擲回 `CArchiveException`，預防您的程式讀取物件的不正確的版本。  
  
 如果您希望 `Serialize` 成員函式可以讀取多個版本，也就是說檔案寫入應用程式的不同版本。您可以使用值 **VERSIONABLE\_SCHEMA** 當做引數傳遞給 `IMPLEMENT_SERIAL` 巨集。  如需使用方式詳細資訊和範例，請參閱類別 `CArchive`的 `GetObjectSchema` 成員函式。  
  
 下列範例顯示如何為類別 `CPerson` 使用 `IMPLEMENT_SERIAL` ，該類別衍生自 `CObject`：  
  
 [!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_4.cpp)]  
  
 一旦您有可序列化類別，您可以序列化類別的物件，如文章 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md) 中所述。  
  
## 請參閱  
 [序列化](../mfc/serialization-in-mfc.md)
---
title: "TN002：持續性物件資料格式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive 類別, 支援持續性資料"
  - "持續性 C++ 物件"
  - "持續性物件資料"
  - "TN002"
  - "VERSIONABLE_SCHEMA 巨集"
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
caps.latest.revision: 22
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN002：持續性物件資料格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註描述支援保存 C\+\+ 物件和目標資料格式的 MFC 常式，會在檔案中儲存。  本章節僅適用於 [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) and [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 巨集的類別。  
  
## 問題  
 持續性資料的 MFC 實作在檔案的連續組件儲存資料的許多物件。  物件的 `Serialize` 方法會將物件的資料成員精簡二進位格式。  
  
 實作來確定使用 [CArchive Class](../mfc/reference/carchive-class.md)，所有資料都儲存在相同的格式儲存。  它會使用 `CArchive` 物件做為轉譯器。  它所建立的物件來保存，直到您呼叫 [CArchive::Close](../Topic/CArchive::Close.md)。  這個方法可以明確呼叫由程式設計人員或隱含的解構函式，當程式結束包含 `CArchive`的範圍。  
  
 這個附註描述 `CArchive` 成員 [CArchive::ReadObject](../Topic/CArchive::ReadObject.md) 和 [CArchive::WriteObject](../Topic/CArchive::WriteObject.md)的實作。  您會發現這些函式的程式碼在 Arcobj.cpp 和 `CArchive` 的主要實作 Arccore.cpp。  使用者程式碼不會直接呼叫 `ReadObject` 和 `WriteObject` 。  相反地，是由 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 巨集產生的類別特定型別安全插入和擷取運算子使用這些物件。  下列程式碼顯示 `WriteObject` 和 `ReadObject` 如何隱含呼叫:  
  
```  
class CMyObject : public CObject  
{  
    DECLARE_SERIAL(CMyObject)  
};  
  
IMPLEMENT_SERIAL(CMyObj, CObject, 1)  
  
// example usage (ar is a CArchive&)  
CMyObject* pObj;  
CArchive& ar;  
ar << pObj;        // calls ar.WriteObject(pObj)  
ar >> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))  
```  
  
## 對存放區 \(CArchive::WriteObject\) 儲存物件  
 用來重建物件的 `CArchive::WriteObject` 方法寫入標頭資料。  這個資料會包含兩個部分:物件的型別和物件的狀態。  這個方法對維護會寫出，因此，只有單一複本儲存，不論指標數目的物件的識別也負責該物件 \(包括圓形指標\)。  
  
 儲存 \(插入\) 和還原 \(由\) 物件取決於幾「資訊清單常數」。這些是二進位儲存並提供重要資訊給封存的值 \(請注意「w」前置詞指令 16 位元的個數\):  
  
|Tag|說明|  
|---------|--------|  
|wNullTag|用於 NULL 物件指標 \(0\)。|  
|wNewClassTag|表示後續的類別描述不熟悉這個封存內容 \(\- 1\)。|  
|wOldClassTag|讀取物件的指示類別在這個內容 \(0x8000\) 看到。|  
  
 當儲存物件時，會從預存物件的對應到 32 位元保存 Identifier \(PID\) 的封存維護 [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) \( `m_pStoreMap`\)。  PID 指派給每一個唯一的物件和儲存在封存中的每個唯一的類別名稱。  這些 PID 是實作的會從 1 開始。.  這些 PID 沒有意義在封存的範圍之外，然後，特別是，不要使用記錄編號或其他識別項的混淆。  
  
 在 `CArchive` 類別， PID 32 位元，不過，它們會寫出，因為 16 位元，除非大於 0x7FFE。  大 PID 寫成 32 位元 PID 遵循的 0x7FFF。  這會維護與在舊版中建立之專案的相容性。  
  
 當提出要求之儲存之項目的物件 \(通常是使用全域插入運算子\)，檢查在空白 [CObject](../mfc/reference/cobject-class.md) 指標進行。  如果指標是 null，則 `wNullTag` 會插入封存資料流。  
  
 如果指標不是空的，而且可以序列化 \(類別是 `DECLARE_SERIAL` 類別\)，程式碼會查看的 `m_pStoreMap` 物件是否已經儲存。  如果有，程式碼插入 32 位元 PID 與該物件保存至資料流。  
  
 如果物件尚未儲存之前，您必須考量下列兩種可能性:或物件和確切型別 \(即類別\) 的物件不熟悉這個封存內容，或者物件已經看的是正確的型別。  若要判斷型別是否已見過，程式碼查詢 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 物件的 `m_pStoreMap` `CRuntimeClass` 物件與儲存的物件相符。  如果有相符項目，則 `WriteObject` 會插入位元是 `wOldClassTag` 和 `OR` 的這個索引標籤。  如果 `CRuntimeClass` 不熟悉這個封存內容， `WriteObject` 指派新的 PID 到該類別並將它插入封存中， `wNewClassTag` 值之後。  
  
 使用 `CRuntimeClass::Store` 方法，這個類別的描述元就會插入封存。  `CRuntimeClass::Store` 插入類別 \(參看下方\) 和類別的 ASCII 文字名稱的結構描述數目。  請注意使用 ASCII 文字名稱並不保證封存的唯一跨應用程式的。  因此，您應該將您的資料檔案會防止損毀。  在類別資訊的外掛程式之後，將物件保存至 `m_pStoreMap` 接著會呼叫 `Serialize` 方法插入類別特定資料。  將物件插入 `m_pStoreMap` 在呼叫 `Serialize` 之前防止物件的多個複本儲存到存放區。  
  
 當傳回至初始呼叫端 \(通常是物件網路\) 時，您必須呼叫 [CArchive::Close](../Topic/CArchive::Close.md)。  如果您打算執行其他 [C 檔案](../mfc/reference/cfile-class.md)作業，您必須呼叫 `CArchive` 方法 [清除](../Topic/CArchive::Flush.md) 防止封存的損毀。  
  
> [!NOTE]
>  這個實作 0x3FFFFFFE 索引一種硬式限制每個封存內容。  這個數字表示可在單一封存儲存唯一的物件和類別的最大數目，不過，單一磁碟檔案可能有不限數目的封存內容。  
  
## 從存放區 \(CArchive::ReadObject\) 載入的物件  
 載入 \(由\) 會使用 `CArchive::ReadObject` 方法是 `WriteObject`計數器。  使用 `WriteObject`， `ReadObject` 不直接由使用者程式碼呼叫;使用者程式碼應該讓呼叫 `ReadObject` 和 `CRuntimeClass`的預期的型別安全擷取運算子。  這樣可確保取作業的類型完整性。  
  
 從 1 開始指派的遞增 PID， `WriteObject` 實作 \(0 預先定義，當 Null 物件\)， `ReadObject` 實作可以使用陣列維護封存內容的狀態。  當 PID 從存放區讀取時，則為，如果 PID 大於 `m_pLoadArray`目前的上限， `ReadObject` 知道新物件 \(或類別描述\) 之後。  
  
## 結構描述的數目。  
 結構描述數字，指派給類別，該類別的 `IMPLEMENT_SERIAL` 方法時，是「Release」類別實作。  結構描述參考類別的實作，則為指定物件可保存的次數 \(通常稱為物件版本\)。  
  
 如果您打算經過一段時間後維護相同類別的不同實作，將結構描述，當您修改物件的 `Serialize` 方法實作會使您撰寫可載入物件儲存使用實作的較舊版本的程式碼。  
  
 `CArchive::ReadObject` 方法將會擲回 [CArchiveException](../mfc/reference/carchiveexception-class.md) ，以便在使用類別描述結構描述數字在記憶體中不同的持續性存放區中遇到結構描述數目。  從這個例外狀況復原不容易。  
  
 您可以使用 `VERSIONABLE_SCHEMA` 結合位元 \( `OR`\) 的結構描述版本避免擲回這個例外狀況。  使用 `VERSIONABLE_SCHEMA`，您的程式碼可以藉由檢查從 [CArchive::GetObjectSchema](../Topic/CArchive::GetObjectSchema.md)的傳回值會在其 `Serialize` 函式的適當動作。  
  
## 直接呼叫序列化  
 在大部分情況下 `WriteObject` 和 `ReadObject` 物件的一般配置的額外負荷不是必要的。  這是常見的情況下將資料還原序列化到 [CDocument](../mfc/reference/cdocument-class.md)。  在這種情況下， `CDocument` 的 `Serialize` 方法直接呼叫，而不使用擷取或插入運算子。  文件的內容可能會使用更一般物件的配置。  
  
 呼叫 `Serialize` 直接有下列優點和缺點:  
  
-   在物件序列化前後，額外位元組不會加入封存。  這不僅可儲存的資料較小，不過，可讓您實作可以處理所有檔案格式的 `Serialize` 處理常式。  
  
-   MFC 調整，因此 `WriteObject` 和 `ReadObject` 實作和相關的集合不會連接至應用程式，除非您需要其他用途的一般物件的配置。  
  
-   您的程式碼不需要從舊結構描述數字復原。  這可讓您的文件序列化程式碼負責輸入結構描述數字，檔案格式的版本號碼，或是任何識別數字併入資料檔的開始使用。  
  
-   將與 `Serialize` 的直接呼叫無法使用 `CArchive::GetObjectSchema` 也必須處理傳回值的任何物件 \(、\) 表示的 1 版是未知的。  
  
 由於 `Serialize` 直接在文件呼叫，為文件的子物件通常不是可對其父文件的封存參考。  必須明確指定這些物件指標其容器文件或您必須使用 [CArchive::MapObject](../Topic/CArchive::MapObject.md) 函式將 `CDocument` 指標 PID，在這些返回指標封存之前。  
  
 如先前所述，您應輸入版本和類別資訊，當您直接呼叫 `Serialize` 時，可讓您之後變更表單，同時保留與舊版檔案時的回溯相容性。  `CArchive::SerializeClass` 函式可以明確呼叫在直接序列化物件之前或是呼叫基底類別的。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
---
title: "CArchive Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive class"
  - "data storage [C++], CArchive class"
  - "I/O [MFC], archiving objects"
  - "序列化 [C++], CArchive class"
  - "storage [C++], CArchive class"
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CArchive Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您將物件複雜網路以保存的一種永久二進位格式 \(通常是磁碟儲存體\)，這些物件在刪除之後。  
  
## 語法  
  
```  
class CArchive  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CArchive::CArchive](../Topic/CArchive::CArchive.md)|建立 `CArchive` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CArchive::Abort](../Topic/CArchive::Abort.md)|關閉一個檔案，而不會擲回例外狀況。|  
|[CArchive::Close](../Topic/CArchive::Close.md)|清除不記錄的資料和中斷與 `CFile`。|  
|[CArchive::Flush](../Topic/CArchive::Flush.md)|清除檔案緩衝區中記錄的資料。|  
|[CArchive::GetFile](../Topic/CArchive::GetFile.md)|取得這個檔案的 `CFile` 物件指標。|  
|[CArchive::GetObjectSchema](../Topic/CArchive::GetObjectSchema.md)|從呼叫 `Serialize` 函式判斷序列化物件的版本。|  
|[CArchive::IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md)|判斷是否已清空緩衝區已在期間通訊端接收處理序的視窗。|  
|[CArchive::IsLoading](../Topic/CArchive::IsLoading.md)|判斷這個檔案是否載入。|  
|[CArchive::IsStoring](../Topic/CArchive::IsStoring.md)|判斷這個是否儲存檔案。|  
|[CArchive::MapObject](../Topic/CArchive::MapObject.md)|在對應中將不會序列化至檔案，但是，請可供子物件中參考的物件。|  
|[CArchive::Read](../Topic/CArchive::Read.md)|讀取原始位元組。|  
|[CArchive::ReadClass](../Topic/CArchive::ReadClass.md)|讀取類別參考先前儲存 `WriteClass`。|  
|[CArchive::ReadObject](../Topic/CArchive::ReadObject.md)|呼叫物件的 `Serialize` 函式。|  
|[CArchive::ReadString](../Topic/CArchive::ReadString.md)|讀取一行文字。|  
|[CArchive::SerializeClass](../Topic/CArchive::SerializeClass.md)|根據 `CArchive`方向讀取或寫入至 `CArchive` 物件的類別參考。|  
|[CArchive::SetLoadParams](../Topic/CArchive::SetLoadParams.md)|設定載入陣列成長到的大小。  必須呼叫，在所有物件載入之前，或在 `MapObject` 或 `ReadObject` 呼叫之前。|  
|[CArchive::SetObjectSchema](../Topic/CArchive::SetObjectSchema.md)|將檔案儲存在物件的結構描述。|  
|[CArchive::SetStoreParams](../Topic/CArchive::SetStoreParams.md)|設定雜湊資料表大小和用來執行對應的區塊大小在序列化過程中辨識唯一的物件。|  
|[CArchive::Write](../Topic/CArchive::Write.md)|寫入未經處理的位元組。|  
|[CArchive::WriteClass](../Topic/CArchive::WriteClass.md)|將 `CArchive`寫入 `CRuntimeClass` 的參考。|  
|[CArchive::WriteObject](../Topic/CArchive::WriteObject.md)|呼叫物件的儲存 `Serialize` 函式。|  
|[CArchive::WriteString](../Topic/CArchive::WriteString.md)|寫入一行文字。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CArchive::operator \<\<](../Topic/CArchive::operator%20%3C%3C.md)|存放區物件和基本型別 \(Primitive Type\) 的檔案。|  
|[CArchive::operator \>\>](../Topic/CArchive::operator%20%3E%3E.md)|載入物件和基本型別從檔案。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CArchive::m\_pDocument](../Topic/CArchive::m_pDocument.md)||  
  
## 備註  
 `CArchive` 不具有基底類別。  
  
 您可以從持續性儲存體載入物件，重新組成它們在記憶體中。  讓資料這個程序稱為「保存序列化」。  
  
 您可以將檔案物件當做一種二進位資料流。  就像輸入\/輸出資料流，檔案與檔案並從儲存區允許緩衝區的文字和資料讀取。  輸入\/輸出資料流 ASCII 字元處理順序，在中，但是檔案處理有效，非多餘的格式的二進位物件資料。  
  
 在中，您可以建立 `CArchive` 物件之前，您必須建立 [C 檔案](../../mfc/reference/cfile-class.md) 物件。  此外，您必須確定檔案的載入\/存放區的狀態與檔案之開啟模式不相容。  您限制為每個檔案中包含一個作用中的檔案。  
  
 當您 `CArchive` 建構物件時，可以將它附加至表示開啟的文件類別 `CFile` \(或衍生類別\) 的物件。  您也可以指定這個檔案是否已載入或儲存要使用。  `CArchive` 物件不僅能處理基本型別，也會對 [CObject](../../mfc/reference/cobject-class.md)\-用於序列化設計的衍生類別。  可序列化類別通常有 `Serialize` 成員函式，因此，它通常會使用 [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) 和 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 巨集，如所述。 `CObject`類別之下。  
  
 多載擷取 \(**\>\>**\) 和插入**\<\<**\(\) 運算子比較便利支援兩個基本型別和 `CObject`衍生類別的檔案程式設計介面。  
  
 `CArchive` 也支援程式設計與 MFC Windows Sockets 類別 [CSocket](../../mfc/reference/csocket-class.md) 和 [CSocketFile](../../mfc/reference/csocketfile-class.md)。  [IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md) 成員函式的使用方式。  
  
 如需 `CArchive`的資訊，請參閱 Microsoft 知識庫文件 [序列化](../../mfc/serialization-in-mfc.md) 和 [Windows Sockets:使用具有檔案的通訊端](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## 繼承階層架構  
 `CArchive`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)
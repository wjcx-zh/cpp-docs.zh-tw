---
title: "CLongBinary Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "BLOB"
  - "CLongBinary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB (二進位大型物件)"
  - "BLOB (二進位大型物件), CLongBinary 類別"
  - "CLongBinary 類別"
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLongBinary Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

simplifies 針對極大型二進位資料在資料庫物件 \(通常稱為 BLOBs 或「二進位大型物件\)。  
  
## 語法  
  
```  
class CLongBinary : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CLongBinary::CLongBinary](../Topic/CLongBinary::CLongBinary.md)|建構 `CLongBinary` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CLongBinary::m\_dwDataLength](../Topic/CLongBinary::m_dwDataLength.md)|在控制項的程式碼在 `m_hData`儲存資料物件的位元組包含實際大小。|  
|[CLongBinary::m\_hData](../Topic/CLongBinary::m_hData.md)|包含視窗控制代碼。 `HGLOBAL` 實際影像物件。|  
  
## 備註  
 例如， \[記錄\] 欄位在 SQL 資料表可能包含表示圖片的點陣圖。  `CLongBinary` 物件儲存這類物件並將它的大小。  
  
> [!NOTE]
>  一般而言，是比較好的作法。 [DFX\_Binary](../Topic/DFX_Binary.md) 函式現在 [CByteArray](../../mfc/reference/cbytearray-class.md) 一起使用。  您仍然可以使用 `CLongBinary`，不過，通常 `CByteArray` 提供更多的功能，在 Win32 中，因為不再具有大小限制遇到具有 16 位元 `CByteArray`。  這項建議適用於程式設計與資料存取物件 \(DAO\) 以及開放式資料庫連接 \(Open Database Connectivity，ODBC\)。  
  
 若要使用 `CLongBinary` 物件，請宣告型別 `CLongBinary` 的欄位資料成員至資料錄集類別中。  當資料錄集建構，成員就會是資料錄集類別中的某個內嵌的成員，並建構。  在 `CLongBinary` 建構物件後，資料錄欄位交換 \(RFX\) 機制從欄位載入資料物件中目前資料錄的資料來源並將它儲存到此資料錄時，已更新資料錄時。  RFX 查詢二進位大型物件大小的資料來源，其配置儲存體 \(透過 `CLongBinary` 物件的 `m_hData` 資料成員\) 和存放區 `HGLOBAL` 控制代碼在 `m_hData`的資料。  RFX 在 `m_dwDataLength` 資料成員也會儲存資料物件的實際大小。  與物件中的資料來傳遞 `m_hData`，使用時通常會使用  視窗中 `HGLOBAL` 控制代碼所儲存之資料的相同的技術。  
  
 當您終結您的資料錄集時，也會終結物件， `CLongBinary` 內嵌，而且其解構函式解除配置 `HGLOBAL` 資料控制代碼。  
  
 如需大型物件並使用 `CLongBinary`的相關資訊，請參閱 Microsoft 知識庫文件 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md) 和 [資料錄集:使用大型資料項目 \(ODBC\) 使用](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## 需求  
 **Header:** afxdb\_.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)
---
title: "CCommand 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CCommand"
  - "CCommand"
  - "ATL.CCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCommand 類別"
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CCommand 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供方法設定和執行命令。  
  
## 語法  
  
```  
template <  
   class TAccessor = CNoAccessor,  
   template < typename T > class TRowset = CRowset,  
   class TMultiple = CNoMultipleResults   
>  
class CCommand :   
   public CAccessorRowset <  
      TAccessor,   
      TRowset   
   >,  
   public CCommandBase,  
   public TMultiple  
```  
  
#### 參數  
 `TAccessor`  
 您想要命令使用該存取子類別的型別 \(例如 `CDynamicParameterAccessor`、 `CDynamicStringAccessor`或 `CEnumeratorAccessor`\) 。  預設值為 `CNoAccessor`，指定類別不支援參數或輸出資料行。  
  
 `TRowset`  
 您想要命令使用該資料列集類別的型別 \(例如 `CArrayRowset`、 `CNoRowset`或 \) 。  預設為 `CRowset`。  
  
 `TMultiple`  
 若要使用可以傳回多項結果的 OLE DB 命令，指定 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)。  否則，請使用 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。  如需詳細資訊，請參閱[IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx)。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[關閉](../../data/oledb/ccommand-close.md)|關閉目前的命令。|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|當使用多項結果時設定時，擷取下一個結果。|  
|[開啟](../../data/oledb/ccommand-open.md)|執行並選擇性地將命令繫結。|  
  
### 繼承的方法  
  
|||  
|-|-|  
|[Create](../../data/oledb/ccommand-create.md)|建立指定之工作階段的新命令，然後設定命令文字。|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|建立新命令。|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|取得命令的參數、其名稱和它們的型別清單。|  
|[準備](../../data/oledb/ccommand-prepare.md)|驗證並最佳化目前命令。|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|如果需要，釋放參數存取子，然後釋放命令。|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|指定每個命令參數的原生型別。|  
|[Unprepare](../../data/oledb/ccommand-unprepare.md)|捨棄目前命令執行計劃。|  
  
## 備註  
 當您需要執行以參數為基礎的作業或執行命令時，可以使用這個類別。  如果您只需要開啟簡單資料列集，請使用 [CTable](../../data/oledb/ctable-class.md) 。  
  
 您使用的存取子類別決定繫結參數和資料方法。  
  
 請注意：您不能將預存程序與 OLE DB Provider for Jet 一起使用，因為該提供者並不支援預存程序 \( 查詢字串中只能使用常數 \)。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)
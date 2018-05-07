---
title: CCommand 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
dev_langs:
- C++
helpviewer_keywords:
- CCommand class
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 667e86c173a7001ae22036cb1f0dd8f3fbfcf6a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ccommand-class"></a>CCommand 類別
提供方法來設定和執行命令。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CNoAccessor,  
          template <typename T> class TRowset = CRowset,  
          class TMultiple = CNoMultipleResults>  
class CCommand :   
           public CAccessorRowset <TAccessor, TRowset>,  
           public CCommandBase,  
           public TMultiple  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別的型別 (例如`CDynamicParameterAccessor`， `CDynamicStringAccessor`，或`CEnumeratorAccessor`) 您想要使用的命令。 預設值是`CNoAccessor`，以指定的類別不支援參數或輸出資料行。  
  
 `TRowset`  
 資料列集類別的型別 (例如`CArrayRowset`或`CNoRowset`) 您想要使用的命令。 預設值為 `CRowset`。  
  
 `TMultiple`  
 若要使用 OLE DB 命令可傳回多個結果，指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否則，請使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 如需詳細資訊，請參閱[IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx)。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[關閉](../../data/oledb/ccommand-close.md)|關閉目前的命令。|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|當使用多個結果集提取下一個結果。|  
|[開啟](../../data/oledb/ccommand-open.md)|執行，並選擇性地將命令繫結。|  
  
### <a name="inherited-methods"></a>繼承的方法  
  
|||  
|-|-|  
|[建立](../../data/oledb/ccommand-create.md)|指定的工作階段中，建立新的命令，然後設定命令文字。|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|建立新的命令。|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|取得命令的參數，其名稱，以及它們的型別清單。|  
|[準備](../../data/oledb/ccommand-prepare.md)|驗證並最佳化目前的命令。|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|釋放參數存取子，如有必要，然後再釋放命令。|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|指定每一個命令參數的原生類型。|  
|[Unprepare](../../data/oledb/ccommand-unprepare.md)|捨棄目前的命令執行計畫。|  
  
## <a name="remarks"></a>備註  
 當您需要執行參數為基礎的作業，或執行命令時，請使用這個類別。 如果您只需要開啟簡單的資料列集，使用[CTable](../../data/oledb/ctable-class.md)改為。  
  
 您要使用的存取子類別會決定參數和資料繫結的方法。  
  
 請注意，您無法使用預存程序與 OLE DB Provider for Jet 因為該提供者不支援預存程序 （允許查詢字串中只有常數）。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
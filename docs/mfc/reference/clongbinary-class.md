---
title: "CLongBinary 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs: C++
helpviewer_keywords: CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49661932192a32550d50edfbbc52d7967cb78dcd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clongbinary-class"></a>CLongBinary 類別
簡化在資料庫中對極大型二進位資料物件 (通常稱為 BLOB 或「二進位大型物件」) 的處理。  
  
## <a name="syntax"></a>語法  
  
```  
class CLongBinary : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](#clongbinary)|建構 `CLongBinary` 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|包含的實際大小，以位元組為單位的資料物件的控制代碼會儲存在`m_hData`。|  
|[CLongBinary::m_hData](#m_hdata)|包含 Windows`HGLOBAL`實際影像物件控制代碼。|  
  
## <a name="remarks"></a>備註  
 例如，SQL 資料表中的記錄欄位可能包含代表圖片的點陣圖。 A`CLongBinary`物件會儲存這類物件並追蹤其大小。  
  
> [!NOTE]
>  一般情況下，它是比較好的作法現在使用[CByteArray](../../mfc/reference/cbytearray-class.md)搭配[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函式。 您仍然可以使用`CLongBinary`，但一般而言`CByteArray`提供更多的功能，在 Win32 中，因為不會遇到的 16 位元的大小限制`CByteArray`。 這項建議適用於資料存取物件 (DAO)，以及開放式資料庫連接 (ODBC) 的程式設計。  
  
 若要使用`CLongBinary`物件，宣告類型的欄位資料成員`CLongBinary`資料錄集類別中。 這個成員會內嵌的類別成員的資料錄集，而且建構資料錄集時，會在建構。 之後`CLongBinary`建構物件、 資料錄欄位交換 (RFX) 機制載入資料物件從目前的記錄資料來源上的欄位，並將它儲存回資料錄，更新記錄時。 RFX 查詢資料來源的二進位大型物件的大小為其配置儲存區 (透過`CLongBinary`物件的`m_hData`資料成員)，並將`HGLOBAL`中的資料處理`m_hData`。 RFX 也會儲存中的資料物件的實際大小`m_dwDataLength`資料成員。 使用中的資料物件，可透過`m_hData`，您通常會用來操作資料儲存在 Windows 中的相同技巧`HGLOBAL`處理。  
  
 當損毀資料錄集，內嵌`CLongBinary`也終結物件，並取消配置其解構函式`HGLOBAL`資料控制代碼。  
  
 如需有關大型物件，以及使用`CLongBinary`，請參閱文章[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)和[資料錄集： 使用大型資料的項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdb_.h  
  
##  <a name="clongbinary"></a>CLongBinary::CLongBinary  
 建構 `CLongBinary` 物件。  
  
```  
CLongBinary();
```  
  
##  <a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength  
 以位元組為單位的資料儲存在儲存的實際大小`HGLOBAL`中處理`m_hData`。  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>備註  
 這個大小可能小於資料配置的記憶體區塊的大小。 呼叫 Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593)函式可取得已配置的大小。  
  
##  <a name="m_hdata"></a>CLongBinary::m_hData  
 儲存 Windows`HGLOBAL`實際的二進位大型物件資料的控制代碼。  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)

---
title: CLongBinary 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs:
- C++
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89eab2862b5a724d1fd55c4d7f0b634b2d5b2e84
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441807"
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
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|包含以位元組為單位的控制代碼會儲存在資料物件的實際大小`m_hData`。|
|[CLongBinary::m_hData](#m_hdata)|包含實際影像物件的 Windows HGLOBAL 控制代碼。|

## <a name="remarks"></a>備註

例如，SQL 資料表中的記錄欄位可能包含代表一張圖片的點陣圖。 A`CLongBinary`物件會儲存這類物件並追蹤其大小。

> [!NOTE]
>  一般情況下，最好現在使用[CByteArray](../../mfc/reference/cbytearray-class.md)搭配[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函式。 您仍然可以使用`CLongBinary`，但一般而言`CByteArray`提供更多的功能，在 Win32 中，因為沒有不再發生 16 位元的大小限制`CByteArray`。 這項建議適用於使用資料存取物件 (DAO)，以及開放式資料庫連接 (ODBC) 進行程式設計。

若要使用`CLongBinary`物件，宣告類型的欄位資料成員`CLongBinary`資料錄集類別中。 這個成員會內嵌的類別成員的資料錄集，而且會在建構資料錄集的建構。 之後`CLongBinary`建構物件、 資料錄欄位交換 (RFX) 機制載入資料物件從資料來源上的目前資料錄的欄位，並將它儲存回資料錄，更新記錄時。 RFX 查詢資料來源的二進位大型物件，大小為其配置儲存區 (透過`CLongBinary`物件的`m_hData`資料成員)，並將`HGLOBAL`中的資料的控制代碼`m_hData`。 RFX 也會將儲存的資料物件的實際大小`m_dwDataLength`資料成員。 使用中的資料物件，可透過`m_hData`，使用您通常會用來操作資料儲存在 Windows 中的相同技巧`HGLOBAL`處理。

當您終結資料錄集，內嵌`CLongBinary`物件終結時也，和其解構函式會取消配置`HGLOBAL`資料控制代碼。

如需大型物件，以及善用`CLongBinary`，請參閱文章[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)並[資料錄集： 使用大型資料的項目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>需求

**標頭：** afxdb_.h

##  <a name="clongbinary"></a>  CLongBinary::CLongBinary

建構 `CLongBinary` 物件。

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

以位元組為單位的 HGLOBAL 控制代碼，以在儲存的資料儲存的實際大小`m_hData`。

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>備註

這個大小可能小於資料配置的記憶體區塊大小。 呼叫 Win32 [GLobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize)函式可取得配置的大小。

##  <a name="m_hdata"></a>  CLongBinary::m_hData

會儲存實際的二進位大型物件資料的 Windows HGLOBAL 控制代碼。

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)

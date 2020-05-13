---
title: CLongBinary 類別
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370128"
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
|[龍二元:CLongBinary](#clongbinary)|建構 `CLongBinary` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|包含其句柄存儲在`m_hData`中 的數據物件的實際大小(以位元組為單位)。|
|[CLongBinary::m_hData](#m_hdata)|包含實際圖像物件的 Windows HGLOBAL 句柄。|

## <a name="remarks"></a>備註

例如,SQL 表中的記錄欄位可能包含表示圖片的位圖。 物件`CLongBinary`存儲此類物件並跟蹤其大小。

> [!NOTE]
> 通常,現在最好將[CByteArray](../../mfc/reference/cbytearray-class.md)與[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函數結合使用。 您仍可以使用`CLongBinary`,但`CByteArray`通常 在 Win32 下提供了更多功能,`CByteArray`因為 16 位 不再遇到大小限制。 此建議適用於資料存取物件 (DAO) 和開放資料庫連接 (ODBC) 程式設計。

要使用`CLongBinary`物件,請聲明記錄集類中類型`CLongBinary`的 欄位數據成員。 此成員將是記錄集類的嵌入成員,將在構造記錄集時構造。 建構`CLongBinary`物件后,記錄欄位交換 (RFX) 機制從數據源上的當前記錄中的欄位載入數據物件,並在更新記錄時將其存儲回記錄。 RFX 查詢二進位大型物件大小的資料來源,為其分配`CLongBinary`存儲(`m_hData`透過對象資料成員`HGLOBAL`),並將句柄`m_hData`儲存到中的數據。 RFX 還會將資料物件的實際大小儲存在資料成員`m_dwDataLength`中 。 使用與通常用於操作儲存在 Windows`m_hData``HGLOBAL`句柄中的數據相同的技術處理對象中的數據。

銷毀記錄集時,嵌入`CLongBinary`的物件也會被銷毀,其析構函數將解構器解分配`HGLOBAL`數據句柄。

有關大型物件和使用的詳細資訊`CLongBinary`,請參閱[記錄集 (ODBC)](../../data/odbc/recordset-odbc.md)和[記錄集:使用大型資料項目 (ODBC) 的文章](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>需求

**標題:** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>龍二元:CLongBinary

建構 `CLongBinary` 物件。

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

以儲存在 HGLOBAL 句柄中的數據的實際大小以`m_hData`位元組 為單位。

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>備註

此大小可能小於為數據分配的記憶體區塊的大小。 呼叫 Win32 [GLobalSize 函數](/windows/win32/api/winbase/nf-winbase-globalsize)以獲取分配的大小。

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary::m_hData

將 Windows HGLOBAL 句柄儲存到實際的二進位大型物件數據。

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)

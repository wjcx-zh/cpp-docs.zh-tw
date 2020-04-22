---
title: CDumpContext 類別
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: e89bbc5f263dc9303140e43914619090109b8315
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753203"
---
# <a name="cdumpcontext-class"></a>CDumpContext 類別

支援使用人類看得懂的格式文字的資料流導向診斷輸出。

## <a name="syntax"></a>語法

```
class CDumpContext
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 轉儲上下文::C 轉儲上下文](#cdumpcontext)|建構 `CDumpContext` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDumpContext::D](#dumpashex)|以十六進位格式轉儲指示的項。|
|[CDumpContext:沖洗](#flush)|刷新轉儲上下文緩衝區中的任何數據。|
|[CDumpContext:取得深度](#getdepth)|獲取與轉儲深度對應的整數。|
|[CDump 上下文:十六進位轉儲](#hexdump)|以十六進位格式轉儲陣列中包含的位元組。|
|[CDump 上下文::設定深度](#setdepth)|設置轉儲的深度。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CDumpContext::運算子&lt;&lt;](#operator_lt_lt)|將變數和對象插入轉儲上下文。|

## <a name="remarks"></a>備註

`CDumpContext`沒有基類。

對於大多數轉儲,您可以使用[afxDump,](diagnostic-services.md#afxdump)一個`CDumpContext`預申報 的物件。 該`afxDump`物件僅在Microsoft基礎類庫的調試版本中可用。

多個記憶體[診斷服務](../../mfc/reference/diagnostic-services.md)用於`afxDump`輸出。

在 Windows 環境下,`afxDump`預先定義物件的輸出在概`cerr`念上與流類似,透過`OutputDebugString`Windows 函數路由到調試器。

類別`CDumpContext`有傾印物件資料的**<<**`CObject`指標的重載插入( ) 運算子。 如果需要派生物件的自訂轉印格式,則重寫[CObject::Dump](../../mfc/reference/cobject-class.md#dump)。 大多數Microsoft 基礎類實現重`Dump`寫的成員函數。

不派生於`CObject`的類(`CString`如`CTime`、`CTimeSpan`和)具有自己的重`CDumpContext`載插入 運算符,通常使用的結構`CFileStatus`(`CPoint`如`CRect`、 和)也具有重載。

如果在類的實現中使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏,則`CObject::Dump`將列印`CObject`派生類的名稱。 否則,它會列印`CObject`。

類`CDumpContext`同時可用於庫的調試版本和發佈版本,`Dump`但成員函數僅在調試版本中定義。 使用 **#ifdef_DEBUG** / `#endif`語句來對診斷代碼(包括自`Dump`定義 成員函數)進行括弧。

在創建自己的`CDumpContext`物件之前,必須創建用作轉儲`CFile`目標的物件。

關於詳細資訊,`CDumpContext`請參考[除錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

**#define_DEBUG**

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDumpContext`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>C 轉儲上下文::C 轉儲上下文

建構類別`CDumpContext`的物件 。

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>參數

*pFile*<br/>
指向作為轉儲目標`CFile`的物件的指標。

### <a name="remarks"></a>備註

物件`afxDump`將自動構造。

轉儲上下文處於活動狀態時,不要`CFile`寫入基礎;否則,您將干擾轉儲。 在 Windows 環境中,輸出通過 Windows 函數`OutputDebugString`路由到調試器。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::D

轉儲格式化為十六進位數字的指定類型。

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>傳回值

`CDumpContext` 物件的參考。

### <a name="remarks"></a>備註

調用此成員函數將指定類型的項轉儲為十六進位數位。 要轉印數組,請呼叫[CDumpContext::十六進位傾印](#hexdump)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext:沖洗

強制將緩衝區中剩餘的任何數據寫入附加到轉儲上下文的檔。

```cpp
void Flush();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext:取得深度

確定深度轉儲還是淺轉儲正在進行中。

```
int GetDepth() const;
```

### <a name="return-value"></a>傳回值

由 設定的傾印的`SetDepth`深度 。

### <a name="example"></a>範例

  請參閱[SetDepth](#setdepth)的範例。

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDump 上下文:十六進位轉儲

轉儲格式化為十六進位數位的位元組。

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>參數

*lpszLine*<br/>
要在新行開始時輸出的字串。

*皮比*<br/>
指向包含要轉儲的位元組的緩衝區的指標。

*n 位元組*<br/>
要轉儲的位元組數。

*n 寬度*<br/>
每行轉儲的最大位元組數(不是輸出線的寬度)。

### <a name="remarks"></a>備註

要將單個特定項類型轉印為十六進位號,請呼叫[CDumpContext::DumpAsHex](#dumpashex)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::運算子&lt;&lt;

將指定的數據輸出到轉儲上下文。

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>傳回值

`CDumpContext` 參考。 使用返回值,可以在一行原始碼上寫入多個插入。

### <a name="remarks"></a>備註

對於`CObject`指標以及大多數基元類型,插入運算符過載。 指向字元的指標會導致字串內容轉儲;指向**void 的**指標僅會導致位址的十六進位轉儲。 LONGLONG 會導致 64 位簽名整數的轉儲;ULONGLONG 會導致64位無符號整數的轉儲。

如果在類的實現中使用IMPLEMENT_DYNAMIC或IMPLEMENT_SERIAL宏,則插入運算符 通過`CObject::Dump`將`CObject`列印 派生類的名稱。 否則,它會列印`CObject`。 如果重寫類`Dump`的函數,則可以提供物件內容的更有意義的輸出,而不是十六進位轉儲。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDump 上下文::設定深度

設置轉儲的深度。

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>參數

*N 紐裡*<br/>
新的深度值。

### <a name="remarks"></a>備註

如果要轉儲不包含指向其他對象的指標的基`CObject`元類型或簡單,則值 0 就足夠了。 大於 0 的值指定一個深轉儲,其中所有物件都遞歸地轉儲。 例如,集合的深層轉儲將轉儲集合的所有元素。 您可以在派生類中使用其他特定深度值。

> [!NOTE]
> 在深轉儲中未檢測到迴圈引用,並可能導致無限迴圈。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)

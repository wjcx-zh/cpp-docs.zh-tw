---
title: Platform::Exception 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: 4604769d9d1bc5fa848d15459327dc87d82f7016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363774"
---
# <a name="platformexception-class"></a>Platform::Exception 類別

表示應用程式執行期間發生的錯誤。 自訂例外狀況類別不能衍生自 `Platform::Exception`類別。 如果您需要自訂例外狀況，您可以使用 `Platform::COMException` 並指定應用程式特定的 HRESULT。

## <a name="syntax"></a>語法

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>成員

`Exception` 類別繼承自 `Object` 類別及 `IException`、 `IPrintable`和 `IEquatable` 介面。

`Exception` 類別也有下列幾種成員。

### <a name="constructors"></a>建構函式

|member|描述|
|------------|-----------------|
|[例外:例外](#ctor)|將 `Exception` 類別的新執行個體初始化。|

### <a name="methods"></a>方法

類別`Exception``Equals()`從[Platform:物件類別](../cppcx/platform-object-class.md)`GetType()``MemberwiseClose()``ToString()``Finalize()`繼承、`GetHashCode()`、 、 、 、 `Exception` 類別也有下列方法。

|member|描述|
|------------|-----------------|
|[異常::建立異常](#createexception)|建立表示指定 HRESULT 值的例外狀況。|

### <a name="properties"></a>屬性

Exception 類別也有下列屬性。

|member|描述|
|------------|-----------------|
|[異常::H 結果](#hresult)|對應於例外狀況的 HRESULT。|
|[例外:消息](#message)|描述例外狀況的訊息。 此值是唯讀，在 `Exception` 建構之後就無法修改。|

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a>異常::建立異常方法

從指定的 HRESULT 值建立 Platform::Exception^。

### <a name="syntax"></a>語法

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>參數

*人力資源*<br/>
HRESULT 值，通常從 COM 方法的呼叫中取得。 如果值為 0(等於S_OK,則此方法將引發[Platform::無效參數異常](../cppcx/platform-invalidargumentexception-class.md),因為成功的 COM 方法不應引發異常。

*訊息*<br/>
描述錯誤的字串。

### <a name="return-value"></a>傳回值

表示錯誤 HRESULT 的例外狀況。

### <a name="remarks"></a>備註

使用這個方法，從傳回的 HRESULT (例如從 COM 介面方法的呼叫中取得) 建立例外狀況。 您可以使用可接受 String^ 參數的多載，提供自訂訊息。

強烈建議使用 CreateException 創建強類型異常,而不是創建僅包含 HRESULT[的平臺::COMexception。](../cppcx/platform-comexception-class.md)

## <a name="exceptionexception-constructor"></a><a name="ctor"></a>例外:異常構造函數

初始化 Exception 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>參數

*h結果*<br/>
由例外狀況表示的錯誤 HRESULT。

*訊息*<br/>
使用者指定的訊息 (例如規範文字)，與例外狀況關聯。 通常您應該最好使用第二個多載，以提供有關發生錯誤的情形和原因、盡可能詳細的描述性訊息。

## <a name="exceptionhresult-property"></a><a name="hresult"></a>例外:hResult 屬性

對應於例外狀況的 HRESULT。

### <a name="syntax"></a>語法

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>屬性值

HRESULT 值。

### <a name="remarks"></a>備註

大部分的例外狀況都是以 HRESULT 值傳回的 COM 錯誤開始。 C++/CX 會將這些值轉換為 Platform::Exception^ 物件，這個屬性儲存原始錯誤碼的值。

## <a name="exceptionmessage-property"></a><a name="message"></a>例外:訊息屬性

描述錯誤的訊息。

### <a name="syntax"></a>語法

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>屬性值

針對肇因於 Windows 執行階段的例外狀況，這是系統提供的錯誤說明。

### <a name="remarks"></a>備註

在 Windows 8 中,此屬性是唯讀的,因為該版本的 Windows 執行時中的異常僅作為 H 結果跨 ABI 傳輸。 在 Windows 8.1 (含) 以後版本，跨 ABI 傳輸更豐富的例外狀況資訊，而且您可以提供其他元件可透過程式設計方式存取的自訂訊息。 有關詳細資訊,請參閱異常[(C++/CX)。](../cppcx/exceptions-c-cx.md)

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

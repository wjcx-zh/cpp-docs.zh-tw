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
ms.openlocfilehash: bfdd8b3df720073e6b4a19cdb5b34db23e659fd0
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741965"
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
|[Exception：： Exception](#ctor)|初始化 `Exception` 類別的新執行個體。|

### <a name="methods"></a>方法

`Exception`類別繼承 `Equals()` `Finalize()` `GetHashCode()` `GetType()` `MemberwiseClose()` `ToString()` [Platform：： Object 類別](../cppcx/platform-object-class.md)的、、、、和方法。 `Exception` 類別也有下列方法。

|member|描述|
|------------|-----------------|
|[Exception：： CreateException](#createexception)|建立表示指定 HRESULT 值的例外狀況。|

### <a name="properties"></a>屬性

Exception 類別也有下列屬性。

|member|描述|
|------------|-----------------|
|[Exception：： HResult](#hresult)|對應於例外狀況的 HRESULT。|
|[Exception：： Message](#message)|描述例外狀況的訊息。 此值是唯讀，在 `Exception` 建構之後就無法修改。|

### <a name="requirements"></a>規格需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a> Exception：： CreateException 方法

從指定的 HRESULT 值建立 Platform::Exception^。

### <a name="syntax"></a>語法

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>參數

*小時*<br/>
HRESULT 值，通常從 COM 方法的呼叫中取得。 如果值為0（等於 S_OK），則這個方法會擲回 [Platform：： InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) ，因為成功的 COM 方法不應該擲回例外狀況。

*message*<br/>
描述錯誤的字串。

### <a name="return-value"></a>傳回值

表示錯誤 HRESULT 的例外狀況。

### <a name="remarks"></a>備註

使用這個方法，從傳回的 HRESULT (例如從 COM 介面方法的呼叫中取得) 建立例外狀況。 您可以使用可接受 String^ 參數的多載，提供自訂訊息。

強烈建議使用 CreateException 來建立強型別例外狀況，而不是建立只包含 HRESULT 的 [Platform：： COMException](../cppcx/platform-comexception-class.md) 。

## <a name="exceptionexception-constructor"></a><a name="ctor"></a> Exception：： Exception 函數

初始化 Exception 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>參數

*hresult*<br/>
由例外狀況表示的錯誤 HRESULT。

*message*<br/>
使用者指定的訊息 (例如規範文字)，與例外狀況關聯。 通常您應該最好使用第二個多載，以提供有關發生錯誤的情形和原因、盡可能詳細的描述性訊息。

## <a name="exceptionhresult-property"></a><a name="hresult"></a> Exception：： HResult 屬性

對應於例外狀況的 HRESULT。

### <a name="syntax"></a>語法

```cpp
public:
    property int HResult { int get(); }
```

### <a name="property-value"></a>屬性值

HRESULT 值。

### <a name="remarks"></a>備註

大部分的例外狀況都是以 HRESULT 值傳回的 COM 錯誤開始。 C++/CX 會將這些值轉換為 Platform::Exception^ 物件，這個屬性儲存原始錯誤碼的值。

## <a name="exceptionmessage-property"></a><a name="message"></a> Exception：： Message 屬性

描述錯誤的訊息。

### <a name="syntax"></a>語法

```cpp
public:property String^ Message;
```

### <a name="property-value"></a>屬性值

針對肇因於 Windows 執行階段的例外狀況，這是系統提供的錯誤說明。

### <a name="remarks"></a>備註

在 Windows 8 中，這個屬性是唯讀的，因為該版本 Windows 執行階段中的例外狀況只會以 HRESULT 傳輸到 ABI。 在 Windows 8.1 (含) 以後版本，跨 ABI 傳輸更豐富的例外狀況資訊，而且您可以提供其他元件可透過程式設計方式存取的自訂訊息。 如需詳細資訊，請參閱 [c + +/cx)  (例外 ](../cppcx/exceptions-c-cx.md)狀況。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

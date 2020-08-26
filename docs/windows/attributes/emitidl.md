---
title: 'emitidl (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 32362f287320e69d1680cbe07ca050143b507514
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846325"
---
# <a name="emitidl"></a>emitidl

指定是否處理所有後續的 IDL 屬性，並將其放在產生的 .idl 檔案中。

## <a name="syntax"></a>語法

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>參數

*state*<br/>
下列其中一個可能的值： **`true`** 、 **`false`** 、 `forced` 、 `restricted` 、 `push` 或 `pop` 。

- 如果 **`true`** 為，則在原始程式碼檔中遇到的任何 idl 分類屬性都會放置在產生的 .idl 檔案中。 這是 **emitidl**的預設設定。

- 如果 **`false`** 為，則在原始程式碼檔中遇到的任何 idl 分類屬性都不會放在產生的 .idl 檔案中。

- 如果 `restricted` 為，則允許在沒有 [module](module-cpp.md) 屬性的檔案中使用 IDL 屬性。 編譯器不會產生 .idl 檔。

- 如果為 `forced` ，則會覆寫後續的 `restricted` 屬性，如果檔案中有 IDL 屬性，則需要檔案有 `module` 屬性。

- `push` 可讓您將目前的 **emitidl** 設定儲存至內部 **emitidl** 堆疊，並 `pop` 讓您將 **emitidl** 設定為內部 **emitidl** 堆疊頂端的任何值。

`defaultimports=`*布林值* \(選擇性) 

- 如果 *布林值* 為 **`true`** ，則會將 docobj.idl 匯入產生的 .idl 檔案。 此外，如果在與 .h 檔案相同的目錄中找到與您在原始程式碼中相同名稱的 .idl 檔案 `#include` ，則產生的 .idl 檔案會包含該 .idl 檔案的匯入語句。

- 如果 *布林值* 為 **`false`** ，docobj.idl 就不會匯入產生的 .idl 檔案。 您必須使用匯 [入](import.md)來明確匯入 .idl 檔。

## <a name="remarks"></a>備註

在原始程式碼檔中遇到 **emitidl** c + + 屬性之後，idl 類別目錄屬性會放在產生的 .idl 檔案中。 如果沒有 **emitidl** 屬性，則會將原始程式碼檔中的 idl 屬性輸出至產生的 .idl 檔案。

原始程式碼檔中可能會有多個 **emitidl** 屬性。 如果 `[emitidl(false)];` 在檔案中遇到但沒有後續的 `[emitidl(true)];` ，則不會將任何屬性處理到產生的 .idl 檔案。

每次編譯器遇到新檔案時， **emitidl** 會隱含地設定為 **`true`** 。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](compiler-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)

---
title: section pragma
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216594"
---
# <a name="section-pragma"></a>section pragma

在 .obj 檔案中建立區段。

## <a name="syntax"></a>語法

> **#pragma 區段 (** "*section-name*" [ **,** *attributes* ] **)**

## <a name="remarks"></a>備註

本文中的詞彙*區段*和*區段*具有相同的意義。

區段定義之後，其仍適用於編譯的其餘部分。 不過, 您必須使用[__declspec (allocate)](../cpp/allocate.md), 否則不會在區段中放置任何內容。

*區段名稱*是必要的參數, 它會成為區段的名稱。 名稱不得與任何標準區段名稱相衝突。 如需建立區段時不應該使用的名稱清單, 請參閱[/SECTION](../build/reference/section-specify-section-attributes.md) 。

*屬性*是選擇性參數, 由一或多個要指派給區段的逗點分隔屬性所組成。 可能的*屬性*為:

|屬性|說明|
|-|-|
|**read**|允許對於資料進行讀取作業。|
|**write**|允許對於資料進行寫入作業。|
|**execute**|允許執行程式碼。|
|**shared**|讓所有載入影像的處理序共用區段。|
|**nopage**|將區段標記為無法分頁。 適用于 Win32 設備磁碟機。|
|**nocache**|將區段標記為不可快取。 適用于 Win32 設備磁碟機。|
|**discard**|將區段標記為可捨棄。 適用于 Win32 設備磁碟機。|
|**remove**|將區段標記為不常駐記憶體。 僅適用于虛擬裝置磁碟機 (V*x*D)。|

如果您未指定任何屬性, 區段就會有**讀取**和**寫入**屬性。

## <a name="example"></a>範例

在此範例中, 第一個區段 pragma 會識別區段及其屬性。 整數`j`不會放入`mysec` , 因為它不是使用`__declspec(allocate)`宣告的。 相反地`j` , 會進入 [資料] 區段。 整數 `i` 屬於 `mysec`，這是其 `__declspec(allocate)` 儲存類別屬性的結果。

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

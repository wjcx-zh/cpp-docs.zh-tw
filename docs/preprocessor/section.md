---
title: section
ms.date: 11/04/2016
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: cd8eee564fa17b21d5421a3471fd676af921f444
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462136"
---
# <a name="section"></a>section

在 .obj 檔案中建立區段。

## <a name="syntax"></a>語法

```
#pragma section( "section-name" [, attributes] )
```

## <a name="remarks"></a>備註

意義*區段*並*一節*是本主題中的可互換的。

區段定義之後，其仍適用於編譯的其餘部分。 不過，您必須使用[__declspec （allocate)](../cpp/allocate.md)或執行任何動作將會放在區段。

*區段名稱*是必要的參數，將會是區段的名稱。 名稱不得與任何標準區段名稱相衝突。 請參閱[/section](../build/reference/section-specify-section-attributes.md)如需建立區段時，應該不會使用您的名稱。

*屬性*是組成一或多個以逗號分隔的屬性，您想要指派給該區段的選擇性參數。 可能*屬性*是：

|屬性|描述|
|-|-|
|**read**|允許對於資料進行讀取作業。|
|**write**|允許對於資料進行寫入作業。|
|**execute**|允許執行程式碼。|
|**shared**|讓所有載入影像的處理序共用區段。|
|**nopage**|將區段標記為不可分頁；適用於 Win32 裝置驅動程式。|
|**nocache**|將區段標記為不可快取；適用於 Win32 裝置驅動程式。|
|**discard**|將區段標記為可捨棄；適用於 Win32 裝置驅動程式。|
|**remove**|標記為不駐留記憶體; 區段虛擬裝置驅動程式 (V*x*D) 只。|

如果您未指定屬性，區段將會具有讀取和寫入屬性。

## <a name="example"></a>範例

在下列範例中，第一個指令會識別區段及其屬性。 由於未以 `j` 宣告整數 `mysec`，因此不會將該整數置於 `__declspec(allocate)`；`j` 會包含在資料區段中。 整數 `i` 屬於 `mysec`，這是其 `__declspec(allocate)` 儲存類別屬性的結果。

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
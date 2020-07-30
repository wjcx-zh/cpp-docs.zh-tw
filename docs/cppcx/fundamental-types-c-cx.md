---
title: 基本類型 (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 3d484d9490a0a5b2ee2e7f92381528124b47701c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230996"
---
# <a name="fundamental-types-ccx"></a>基本類型 (C++/CX)

除了 standard c + + 內建類型之外，c + +/CX 也支援 Windows 執行階段架構所定義的類型系統，方法是提供對應至標準 c + + 類型之 Windows 執行階段基本類型的 typedef。 C + +/CX 會執行布林值、字元和數值基本類型。 這些 Typedef 在 `default` 命名空間中已定義，永遠不需要明確指定。 此外，c + +/CX 還提供特定 Windows 執行階段類型和介面的包裝函式和具體的執行。

## <a name="boolean-and-character-types"></a>布林值和字元類型

下表列出內建布林值和字元類型，以及其 Standard C++ 對應項。

|命名空間|C + +/CX 名稱|定義|Standard C++ 名稱|值的範圍|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|平台|Boolean|8 位元布林值。|bool|**`true`**（非零）和 **`false`** （零）|
|預設|char16|表示 Unicode (UTF-16) 字碼指標的 16 位元非數值。|wchar_t<br /><br /> -或-<br /><br /> L'c'|(依 Unicode 標準指定)|

## <a name="numeric-types"></a>數值類型

下表列出內建數值類型。 數值類型在 `default` 命名空間中宣告，且為對應 C++ 內建類型的 Typedef。 Windows 執行階段中不支援所有的 c + + 內建類型（例如，long）。 為求一致且清楚明瞭，建議您使用 c + +/CX 名稱。

|C + +/CX 名稱|定義|Standard C++ 名稱|值的範圍|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|8 位元帶正負號的數值。|signed char|-128 到127|
|uint8|8 位元不帶正負號的數值。|unsigned char|0 到 255|
|int16|16 位元帶正負號的整數。|short|-32768 到32767|
|uint16|16 位元不帶正負號的整數。|unsigned short|0 到 65,535|
|int32|32 位元帶正負號的整數。|int|-2147483648 到2147483647|
|uint32|32 位元不帶正負號的整數。|不帶正負號的整數|0 到 4,294,967,295|
|int64|64 位元帶正負號的整數。|長時間或 __int64|-9223372036854、775808到9223372036854775807|
|uint64|64 位元不帶正負號的整數。|不帶正負號的長長時間或不帶正負號的 __int64|0 到 18,446,744,073,709,551,615|
|float32|32 位元 IEEE 754 浮點數。|FLOAT|3.4E +/- 38 (7 位數)|
|float64|64 位元 IEEE 754 浮點數。|double|1.7E +/- 308 (15 位數)|

## <a name="windows-runtime-types"></a>Windows 執行階段類型

下表列出 Windows 執行階段架構所定義且內建在 c + +/CX。中的一些額外類型。 物件和字串是參考類型。 其他則為實值類型。 這些類型全部在 `Platform` 命名空間中宣告。 如需完整清單，請參閱 [Platform namespace](../cppcx/platform-namespace-c-cx.md)。

|名稱|定義|
|----------|----------------|
|Object|表示任何 Windows 執行階段類型。|
|String|一系列代表文字的字元。|
|Rect|四個浮點數的組合，代表矩形的位置和大小。|
|SizeT|一對排序的浮點數，指定高度和寬度。|
|Point|一對排序的浮點 X 座標和 Y 座標，定義二維平面中的點。|
|Guid|作為唯一識別項的 128 位元非數值。|
|UIntPtr|（僅供內部使用）。當做指標使用的不帶正負號64位值。|
|IntPtr|（僅供內部使用）。 用來做為指標的帶正負號的64位值。|

## <a name="see-also"></a>另請參閱

[型別系統](../cppcx/type-system-c-cx.md)

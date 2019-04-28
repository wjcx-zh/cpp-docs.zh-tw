---
title: 基本類型 (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 2bd5be01b868fd3086c2064edfd4ca343db425be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301446"
---
# <a name="fundamental-types-ccx"></a>基本類型 (C++/CX)

除了標準C++內建類型， C++/CX 支援型別系統所提供的 typedef，Windows 執行階段基本類型對應至標準的 Windows 執行階段的架構定義C++類型... C++/CX 實作布林值、 字元和數值基本類型。 這些 Typedef 在 `default` 命名空間中已定義，永遠不需要明確指定。 此外， C++/CX 提供特定的 Windows 執行階段型別和介面的包裝函式和具象實作。

## <a name="boolean-and-character-types"></a>布林值和字元類型

下表列出內建布林值和字元類型，以及其 Standard C++ 對應項。

|命名空間|C++/CX 名稱|定義|Standard C++ 名稱|值的範圍|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|平台|Boolean|8 位元布林值。|bool|**真**（非零） 和**false** （零）|
|default|char16|表示 Unicode (UTF-16) 字碼指標的 16 位元非數值。|wchar_t<br /><br /> -或-<br /><br /> L'c'|(依 Unicode 標準指定)|

## <a name="numeric-types"></a>數值類型

下表列出內建數值類型。 數值類型在 `default` 命名空間中宣告，且為對應 C++ 內建類型的 Typedef。 並非所有C++在 Windows 執行階段支援內建類型 (例如 long)。 為了一致性和避免困擾，我們建議您使用C++/CX 名稱。

|C++/CX 名稱|定義|Standard C++ 名稱|值的範圍|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|8 位元帶正負號的數值。|signed char|-128 到 127|
|uint8|8 位元不帶正負號的數值。|unsigned char|0 到 255|
|int16|16 位元帶正負號的整數。|short|-32,768 到 32,767|
|uint16|16 位元不帶正負號的整數。|unsigned short|0 到 65,535|
|int32|32 位元帶正負號的整數。|int|-2,147,483,648 到 2,147,483,647|
|uint32|32 位元不帶正負號的整數。|unsigned int|0 到 4,294,967,295|
|int64|64 位元帶正負號的整數。|long long  -or- __int64|-9,223,372,036,854、 透過 9,223,372,036,854,775,807 775,808|
|uint64|64 位元不帶正負號的整數。|不帶正負號的 long long-或-不帶正負號的 __int64|0 到 18,446,744,073,709,551,615|
|float32|32 位元 IEEE 754 浮點數。|float|3.4E +/- 38 (7 位數)|
|float64|64 位元 IEEE 754 浮點數。|double|1.7E +/- 308 (15 位數)|

## <a name="windows-runtime-types"></a>Windows 執行階段類型

下表列出一些額外的類型由 Windows 執行階段架構所定義且內建於C++/CX。 物件和字串是參考類型。 其他則為實值類型。 這些類型全部在 `Platform` 命名空間中宣告。 如需完整清單，請參閱 [Platform namespace](../cppcx/platform-namespace-c-cx.md)。

|名稱|定義|
|----------|----------------|
|Object|代表任何 Windows 執行階段型別。|
|String|一系列代表文字的字元。|
|Rect|四個浮點數的組合，代表矩形的位置和大小。|
|SizeT|一對排序的浮點數，指定高度和寬度。|
|點|一對排序的浮點 X 座標和 Y 座標，定義二維平面中的點。|
|Guid|作為唯一識別項的 128 位元非數值。|
|UIntPtr|(僅供內部使用。)作為指標的不帶正負號 64 位元值。|
|IntPtr|(僅供內部使用。)作為指標的帶正負號 64 位元值。|

## <a name="see-also"></a>另請參閱

[類型系統](../cppcx/type-system-c-cx.md)

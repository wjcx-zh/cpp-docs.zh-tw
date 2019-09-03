---
title: warning pragma
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: 9a79f0c4a9eed6b62e42f056f9d1994b44b57297
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216468"
---
# <a name="warning-pragma"></a>warning pragma

啟用選擇性修改編譯器警告訊息的行為。

## <a name="syntax"></a>語法

> **#pragma 警告 (** \
> &nbsp;&nbsp;&nbsp;&nbsp;*warning-規範* **:** *警告-數位-清單*\
> &nbsp;&nbsp;&nbsp;&nbsp;[ **;** *warning-規範* **:** *警告-數位-清單*...] **)** \
> **#pragma 警告 (push** [ **,** *n* ] **)** \
> **#pragma 警告 (pop)**

## <a name="remarks"></a>備註

以下是可用的警告指定名稱參數。

|警告指定名稱|意義|
|------------------------|-------------|
|*1、2、3、4*|將指定的層級套用至指定的警告。 也會開啟預設為關閉的指定警告。|
|*default*|將警告行為重設為預設值。 也會開啟預設為關閉的指定警告。 警告會以其記載的預設層級產生。<br /><br /> 如需詳細資訊, 請參閱[預設為關閉的編譯器警告](../preprocessor/compiler-warnings-that-are-off-by-default.md)。|
|*disable*|不要發出指定的警告訊息。|
|*error*|將指定的警告回報為錯誤。|
|*once*|只顯示指定的訊息一次。|
|*suppress*|將 pragma 的目前狀態推送到堆疊上，停用為下一行指定的警告，然後推出警告堆疊以重設 pragma 狀態。|

下列程式碼陳述式將說明 `warning-number-list` 參數可以包含多個警告編號，而且可以在相同的 pragma 指示詞中指定多個 `warning-specifier` 參數。

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

這個指示詞在功能上相當於下列程式碼:

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

編譯器會將 0 和 999 之間的任何警告編號加上 4000。

對於在 4700-4999 範圍內的警告編號 (也就是與程式碼產生相關聯的編號)，編譯器遇到函式的左大括號時生效的警告狀態，也會對函式的其餘部分生效。 在函式中使用**warning** pragma 來變更大於4699的警告編號狀態, 只會在函式的結尾之後生效。 下列範例會顯示**警告**pragma 的正確位置, 以停用程式碼產生警告訊息, 然後將它還原。

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

請注意, 在整個函式主體中, **warning** pragma 的最後一項設定會在整個函式中生效。

## <a name="push-and-pop"></a>Push 和 Pop

**Warning** pragma 也支援下列語法, 其中*n*代表警告層級 (1 到 4)。

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Pragma `warning( push )`會儲存每個警告的目前警告狀態。 Pragma `warning( push, n )`會儲存每個警告的目前狀態, 並將全域警告層級設為*n*。

Pragma `warning( pop )`會彈出推送到堆疊上的最後一個警告狀態。 您對*推送*和*pop*之間的警告狀態所做的任何變更都會復原。 請考量以下範例：

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

在此程式碼結束時, *pop*會將每個警告的狀態 (包括4705、4706和 4707) 還原為程式碼開始時的狀態。

當您寫入標頭檔時, 可以使用*push*和*pop*來確保使用者所做的警告狀態變更不會使標頭無法正確編譯。 在標頭開頭使用*push* , 並在結尾處使用*pop* 。 例如, 如果您的標頭未在警告層級4明確編譯, 下列程式碼會將警告層級變更為 3, 然後在標頭結尾還原原始的警告層級。

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

如需可協助您隱藏警告之編譯器選項的詳細資訊, 請參閱[/fi](../build/reference/fi-name-forced-include-file.md)和[/w](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

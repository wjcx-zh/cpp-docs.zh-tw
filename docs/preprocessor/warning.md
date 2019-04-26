---
title: warning
ms.date: 11/04/2016
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: 1341472af22582635207a2bdff93b4367fd59330
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179928"
---
# <a name="warning-pragma"></a>警告 Pragma
啟用選擇性修改編譯器警告訊息的行為。

## <a name="syntax"></a>語法

```
#pragma warning(
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )
#pragma warning( push[ ,n ] )
#pragma warning( pop )
```

## <a name="remarks"></a>備註

以下是可用的警告指定名稱參數。

|警告指定名稱|意義|
|------------------------|-------------|
|*1, 2, 3, 4*|將指定的層級套用至指定的警告。 這樣也會開啟預設為關閉的指定警告。|
|*default*|將警告行為重設為預設值。 這樣也會開啟預設為關閉的指定警告。 警告會以其記載的預設層級產生。<br /><br /> 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../preprocessor/compiler-warnings-that-are-off-by-default.md)。|
|*disable*|不發出指定的警告訊息。|
|*error*|將指定的警告回報為錯誤。|
|*once*|只顯示指定的訊息一次。|
|*suppress*|將 pragma 的目前狀態推送到堆疊上，停用為下一行指定的警告，然後推出警告堆疊以重設 pragma 狀態。|

下列程式碼陳述式將說明 `warning-number-list` 參數可以包含多個警告編號，而且可以在相同的 pragma 指示詞中指定多個 `warning-specifier` 參數。

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

這項功能相當於下列程式碼。

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

編譯器會將 0 和 999 之間的任何警告編號加上 4000。

對於在 4700-4999 範圍內的警告編號 (也就是與程式碼產生相關聯的編號)，編譯器遇到函式的左大括號時生效的警告狀態，也會對函式的其餘部分生效。 使用**警告**pragma 變更編號大於 4699 警告的狀態函式中才會生效之後函式結尾。 下列範例顯示的正確放置**警告**pragma 來停用程式碼產生警告訊息，然後將它還原。

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

請注意，在整個函式主體，最後一項設定**警告**pragma 將整個函式會生效。

## <a name="push-and-pop"></a>Push 和 Pop

**警告**pragma 也支援下列語法，其中*n*代表警告層級 (1 到 4)。

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Pragma`warning( push )`會儲存目前的警告狀態，每個警告。 Pragma`warning( push, n )`每個警告的目前狀態儲存，並將全域警告層級設定為*n*。

Pragma`warning( pop )`的最後警告狀態推入堆疊的 pop。 您對警告狀態之間的任何變更*推播*並*pop*都會復原。 請考量以下範例：

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

在這段程式碼中，結尾處*pop*還原每個警告的狀態 （包括 4705、 4706 和 4707） 到程式碼的開頭。

當您撰寫標頭檔時，您可以使用*推播*並*pop*保證，警告狀態的使用者所做的變更不會防止標頭正確編譯。 使用*推播*開頭的標頭並*pop*結尾。 例如，如果您的標頭未在警告層級 4 清楚編譯，則下列程式碼會將警告層級變更為 3，然後在標頭結尾還原為原始警告層級。

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

如需編譯器選項可協助您隱藏警告，請參閱[/FI](../build/reference/fi-name-forced-include-file.md)並[/w](../build/reference/compiler-option-warning-level.md)。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
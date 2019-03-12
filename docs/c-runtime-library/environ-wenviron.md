---
title: _environ、_wenviron
ms.date: 11/04/2016
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
ms.openlocfilehash: 56f6f1d06d834ccab68daf859fac065cf215582c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748919"
---
# <a name="environ-wenviron"></a>_environ、_wenviron

`_environ` 變數是指標，指向多位元組字元字串之指標的陣列，而該字串構成此處理序環境。 這個全域變數已由更安全的版本 [getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) 和 [_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md) 所取代，這些應該用來取代全域變數。 `_environ` 在 Stdlib.h 中宣告。

> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```
extern char **_environ;
```

## <a name="remarks"></a>備註

在使用 `main` 函式的程式中，根據作業系統環境上擷取的設定，會在程式啟動時初始化 `_environ`。 此環境包含該形式的一或多個項目。

`ENVVARNAME` `=string`

`getenv_s` 和 `putenv_s` 使用 `_environ` 變數來存取和修改環境資料表。 在呼叫 `_putenv` 以加入或刪除環境設定時，此環境資料表會變更大小。 其在記憶體中的位置也可能會變更，視程式的記憶體需求而定。 `_environ` 的值會自動隨之調整。

`_wenviron` 變數，在 Stdlib.h 中宣告如下：

```
extern wchar_t **_wenviron;
```

這是 `_environ` 的寬字元版本。 在使用 `wmain` 函式的程式中，根據作業系統環境上擷取的設定，會在程式啟動時初始化 `_wenviron`。

在使用 `main` 的程式中，`_wenviron` 一開始是 **NULL**，因為此環境由多位元組字元字串所組成。 在對於 `_wgetenv` 或 `_wputenv` 的第一次呼叫時，會由 `_wenviron` 建立對應的寬字元字串環境並指向此環境。

同樣地，在使用 `wmain` 的程式中，`_environ` 一開始是 **NULL**，因為此環境由寬字元字串所組成。 在對於 `_getenv` 或 `_putenv` 的第一次呼叫時，會由 `_environ` 建立對應的多位元組字元字串環境並指向此環境。

當此環境的兩個複本 (MBCS 和 Unicode) 在此程式中同時存在時，這個執行階段系統必須同時維護兩份複本，造成執行時間較慢。 例如，每當您呼叫 `_putenv` 時，也會自動執行對 `_wputenv` 的呼叫，使得這兩個環境字串對應。

> [!CAUTION]
>  在罕見情況下，當這個執行階段系統正同時維護此環境的 Unicode 版本和多位元組版本時，這兩個環境版本可能無法完全對應。 這是因為雖然任何唯一的多位元組字元字串會對應到唯一的 Unicode 字串，但從唯一的 Unicode 字串對應到多位元組字元字串並不一定唯一。 因此，兩個不同的 Unicode 字串可能對應至相同的多位元組字串。

當使用 [/MD](../build/reference/md-mt-ld-use-run-time-library.md) 或 `/MDd` 連結時，在 Unicode 內容中輪詢 `_environ` 是無意義的。 對於此 CRT DLL，該程式的類型 (寬或多位元組) 是未知的。 因為多位元組類型最可能的情節，所以只建立多位元組類型。

下列虛擬程式碼說明這件事如何發生。

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

在用於此範例的標記法中，此字元字串不是 C 字串常值；相反地，它們是預留位置，代表在 `_wputenv` 呼叫中的 Unicode 環境字串常值和在 `putenv` 呼叫中的多位元組環境字串。 在兩個不同 Unicode 環境字串中的字元預留位置 '`x`' 和 '`y`' 並不會唯一對應至目前 MBCS 中的字元。 相反地，這兩種都會對應至某個 MBCS 字元 '`z`'，此為嘗試轉換該字串的預設結果。

因此，在多位元組環境中，在第一次對 `putenv` 的隱含呼叫後，"`env_var_z`" 的值可能是 "`string1`"，但是當 "`env_var_z`" 的值設定為 "`string2`" 時，可能會在第二次對 `putenv` 的隱含呼叫時覆寫這個值。 因此 Unicode 環境 (在 `_wenviron` 中) 和多位元組環境 (在 `_environ` 中) 可能會在這一系列的呼叫後有所不同。

## <a name="see-also"></a>另請參閱

[全域變數](../c-runtime-library/global-variables.md)<br/>
[getenv、_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)

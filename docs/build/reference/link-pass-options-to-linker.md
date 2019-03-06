---
title: /link (傳遞選項給連結器)
ms.date: 11/04/2016
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: f5e57a19f337653cdab6f66404b9458e1e7fed0d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412831"
---
# <a name="link-pass-options-to-linker"></a>/link (傳遞選項給連結器)

將一或多個連結器選項傳遞給連結器。

## <a name="syntax"></a>語法

```
/link linkeroptions
```

## <a name="arguments"></a>引數

*linkeroptions*<br/>
連結器選項或要傳遞至連結器選項。

## <a name="remarks"></a>備註

**/Link>** 選項和其連結器選項必須出現在任何檔案名稱和 CL 選項之後。 之間的空間，須 **/link>** 和`linkeroptions`。 如需詳細資訊，請參閱 <<c0> [ 設定連結器選項](../../build/reference/setting-linker-options.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 [連結器屬性頁]。

1. 修改一或多個屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 這個編譯器選項不能以程式設計方式變更。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)

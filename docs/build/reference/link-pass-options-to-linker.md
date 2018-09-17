---
title: -link （傳遞選項給連結器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 663407e4948ebc4e3c0a1676c44e8d2b4bd53fcc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704115"
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
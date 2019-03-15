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
ms.openlocfilehash: 7f40841b82db9f46019ce2a96a61a1a0f622b6d5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813431"
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

**/Link>** 選項和其連結器選項必須出現在任何檔案名稱和 CL 選項之後。 之間的空間，須 **/link>** 和`linkeroptions`。 如需詳細資訊，請參閱 < [MSVC 連結器參考](linking.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 [連結器屬性頁]。

1. 修改一或多個屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 這個編譯器選項不能以程式設計方式變更。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)

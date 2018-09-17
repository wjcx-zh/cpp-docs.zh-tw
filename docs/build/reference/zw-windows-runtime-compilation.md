---
title: -ZW （Windows 執行階段編譯） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f793db1bf227006c4278eff55ce53092a864aa83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700943"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Windows 執行階段編譯)

編譯原始程式碼，以支援 Visual c + + 元件擴充功能中 C + + /CX for 建立通用 Windows 平台 (UWP) 應用程式。

當您使用 **/ZW**編譯時，一律指定 **/EHsc**以及。

## <a name="syntax"></a>語法

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>引數

**nostdlib**<br/>
表示 Platform.winmd、Windows.Foundation.winmd 和其他預設 Windows 中繼資料 (.winmd) 檔案未自動包含在編譯中。 相反地，您必須使用[/FU (命名強制 #using 檔案)](../../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，來明確指定 Windows 中繼資料檔案。

## <a name="remarks"></a>備註

當您指定 **/ZW**選項，則編譯器支援下列功能：

- 必要的中繼資料檔案、 命名空間、 資料類型，以及應用程式需要 Windows 執行階段中執行的函式。

- Windows 執行階段物件的參考計數 」 和 「 自動捨棄物件參考計數歸零時自動。

由於 incremental linker 不支援使用包含在.obj 檔案中的 Windows 中繼資料 **/ZW**選項時， [/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)選項與不相容 **/ZW**.

如需詳細資訊，請參閱 < [Visual c + + 語言參考](../../cppcx/visual-c-language-reference-c-cx.md)。

## <a name="requirements"></a>需求

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
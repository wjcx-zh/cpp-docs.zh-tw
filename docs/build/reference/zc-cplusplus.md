---
title: /Zc:__cplusplus （啟用更新的 __cplusplus 巨集）
ms.custom: ''
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:__cplusplus
dev_langs:
- C++
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a796794c0086b09c15ee88442e0fea4d1b114d98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705709"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus （啟用更新的 __cplusplus 巨集）

**/Zc:__cplusplus**編譯器選項會啟用 **\_ \_cplusplus**前置處理器巨集，以報告新的 c + + 語言標準支援更新的值。 根據預設，Visual Studio 一定會傳回"199711 L"的 **\_ \_cplusplus**前置處理器巨集。

## <a name="syntax"></a>語法

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>備註

**\_ \_Cplusplus**前置處理器巨集通常用來報告支援特定版本的 c + + 標準。 許多現有的程式碼看起來比對"199711 L"這個巨集的值而定，因為編譯器不會變更值的巨集除非您明確選擇加入的使用 **/Zc:__cplusplus**編譯器選項。 **/Zc:__cplusplus**選項可用以啟動 Visual Studio 2017 版本 15.7，並預設為關閉。 在舊版的 Visual Studio，並根據預設，或者如果 **/Zc:__cplusplus-** 指定時，Visual Studio 會傳回"199711 L"的值為 **\_ \_cplusplus**前置處理器巨集。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會啟用 **/Zc:__cplusplus**。

當 **/Zc:__cplusplus**啟用選項時，所報告的值 **\_ \_cplusplus**巨集取決於[/std](std-specify-language-standard-version.md)切換版本設定。 下表顯示可能的值為巨集：

|/Zc:__cplusplus 交換器|/std:c++ 交換器|__cplusplus 值|
|-|-|-|
Zc:__cplusplus|/std:c + + 14 （預設值）|201402 L
Zc:__cplusplus|/std:c + + 17|201703 L
Zc:__cplusplus|/std:c + + 最新|201704 L
Zc:__cplusplus-（停用）|任何值|199711 L
未指定|任何值|199711 L

編譯器不支援 C + + 98、 C + + 03 中，或 C + + 11 標準交換器。

將偵測進行更精細的編譯器工具組變更，使用[_MSC_VER](../../preprocessor/predefined-macros.md)預先定義巨集。 此內建的巨集的值會遞增每個工具組中更新 Visual Studio 2017 和更新版本。 [_MSVC_LANG](../../preprocessor/predefined-macros.md)預先定義巨集是否報告標準版本 **/Zc:__cplusplus**選項已啟用或停用。 當 **/Zc:__cplusplus**已啟用， `__cplusplus == _MSVC_LANG`。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 新增 **/Zc:__cplusplus**或 **/Zc:__cplusplus-** 至**其他選項：** 窗格。

## <a name="see-also"></a>另請參閱

- [/Zc (一致性)](zc-conformance.md)
- [/std （指定語言標準版）](std-specify-language-standard-version.md)
- [預先定義巨集](../../preprocessor/predefined-macros.md)

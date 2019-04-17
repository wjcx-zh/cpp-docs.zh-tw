---
title: '/Zc: __cplusplus （啟用更新的 __cplusplus 巨集）'
ms.date: 05/30/2018
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 89545f541f32374a47dce7f87958e61873c1b47c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810090"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc: __cplusplus （啟用更新的 __cplusplus 巨集）

**/Zc: __cplusplus**編譯器選項會啟用 **\_ \_cplusplus**回報最新的 c + + 語言標準支援的更新的值的前置處理器巨集。 根據預設，Visual Studio 一律會傳回值"199711 L"  **\_ \_cplusplus**前置處理器巨集。

## <a name="syntax"></a>語法

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>備註

**\_\_Cplusplus** 前置處理器巨集通常用來報告支援特定版本的 c + + 標準。 因為許多現有的程式碼看起來比對"199711 L"這個巨集的值而定，編譯器不會變更巨集的值，除非明確地在您選擇使用 **/zc: __cplusplus**編譯器選項。 **/Zc: __cplusplus**選項可用以啟動 Visual Studio 2017 15.7 版中，並預設為關閉。 在舊版的 Visual Studio，並根據預設，或如果 **/Zc:__cplusplus-** 指定時，Visual Studio 會傳回"199711 L"的值為 **\_ \_cplusplus**前置處理器巨集。 [/Permissive--](permissive-standards-conformance.md)選項不會啟用 **/zc: __cplusplus**。

當 **/zc: __cplusplus**啟用選項時，所報告的值 **\_ \_cplusplus**巨集取決於[/std](std-specify-language-standard-version.md)切換版本設定。 下表顯示可能的值為巨集：

|/Zc: __cplusplus 參數|/std:c++ 交換器|__cplusplus value|
|-|-|-|
Zc:__cplusplus|/std: c + + 14 （預設值）|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus-（停用）|任何值|199711L
未指定|任何值|199711L

編譯器不支援 C + + 98、 C + + 03，或 C + + 11 標準交換器。

更精細的編譯器工具組的變更偵測，請使用[_MSC_VER](../../preprocessor/predefined-macros.md)預先定義的巨集。 此內建的巨集的值會遞增每個工具組中更新 Visual Studio 2017 和更新版本。 [_MSVC_LANG](../../preprocessor/predefined-macros.md)預先定義的巨集報告標準的版本是否 **/zc: __cplusplus**選項已啟用或停用。 當 **/zc: __cplusplus**已啟用， `__cplusplus == _MSVC_LANG`。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 新增 **/zc: __cplusplus**或是 **/Zc:__cplusplus-** 來**其他選項：** 窗格。

## <a name="see-also"></a>另請參閱

- [/Zc (一致性)](zc-conformance.md)
- [/std （指定語言標準版本）](std-specify-language-standard-version.md)
- [預先定義巨集](../../preprocessor/predefined-macros.md)

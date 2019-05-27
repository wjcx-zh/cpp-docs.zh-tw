---
title: /Zc:__cplusplus (啟用已更新的 __cplusplus 巨集)
ms.date: 05/16/2019
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 43392438eabc7cc7f6decb1349d112a0ce5bd0f5
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837543"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (啟用已更新的 __cplusplus 巨集)

**/Zc:__cplusplus** 編譯器會啟用 **\_\_cplusplus** 前置處理器巨集，以回報最近 C++ 語言標準支援的已更新值。 根據預設，Visual Studio 一律會針對 **\_\_cplusplus** 前置處理器巨集傳回值 "199711L"。

## <a name="syntax"></a>語法

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>備註

**\_\_cplusplus** 前置處理器巨集通常會用來回報特定 C++ 標準版本的支援。 由於許多現有程式碼都看似相依於符合 "199711L" 的此巨集值，因此編譯器不會變更巨集的值，除非您明確地使用 **/Zc:__cplusplus** 編譯器選項來做選擇。 **/Zc:__cplusplus** 選項已在 Visual Studio 2017 15.7 版中開始提供，並預設為關閉。 在舊版 Visual Studio 中的預設中，或是指定 **/Zc:__cplusplus-**，Visual Studio 都會針對 **\_\_cplusplus** 前置處理器巨集傳回值 "199711L"。 [/permissive-](permissive-standards-conformance.md) 選項不會啟用 **/Zc:__cplusplus**。

當 **/Zc:__cplusplus** 選項啟用後，**\_\_cplusplus** 巨集所回報的值會相依於 [/std](std-specify-language-standard-version.md) 版本參數設定。 下表顯示巨集的可能值：

|/Zc:__cplusplus 參數|/std:c++ 參數|__cplusplus 值|
|-|-|-|
Zc:__cplusplus|/std:c++14 (預設值)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus- (已停用)|任何值|199711L
未指定|任何值|199711L

編譯器不支援 C++98、C++03 或 C++11 的標準參數。

若要更精細地偵測編譯器工具組的變更，請使用 [_MSC_VER](../../preprocessor/predefined-macros.md) 預先定義巨集。 此內建巨集的值會隨著 Visual Studio 2017 和更新版本中的每個工具組更新進行累加。 [_MSVC_LANG](../../preprocessor/predefined-macros.md) 預先定義巨集會回報 **/zc: __cplusplus** 選項啟用或停用時的標準版本。 當 **/Zc:__cplusplus** 啟用時，`__cplusplus == _MSVC_LANG`。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 將 **/Zc:__cplusplus** 或 **/Zc:__cplusplus-** 新增至 [其他選項：] 窗格。

## <a name="see-also"></a>另請參閱

- [/Zc (一致性)](zc-conformance.md)
- [/std (指定語言標準版本)](std-specify-language-standard-version.md)
- [預先定義巨集](../../preprocessor/predefined-macros.md)

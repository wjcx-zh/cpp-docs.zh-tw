---
title: /PROFILE (效能工具分析工具)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 23cbccba9a8ec839252d553cc5cbafd37e66bbf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320197"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (效能工具分析工具)

產生可與效能工具分析工具搭配使用的輸出檔。

## <a name="syntax"></a>語法

```
/PROFILE
```

## <a name="remarks"></a>備註

/ 設定檔表示下列連結器選項：

- [/OPT:REF](opt-optimizations.md)

- /OPT:NOICF

- [/INCREMENTAL:NO](incremental-link-incrementally.md)

- [/FIXED:NO](fixed-fixed-base-address.md)

/ 設定檔會使連結器在程式映像產生重新配置區段。  重新配置 區段可讓分析工具來轉換程式映像，以取得設定檔資料。

**/ 設定檔**僅只適用於 Enterprise （小組開發） 版本。  如需有關 PREfast 的詳細資訊，請參閱[適用於 C 的程式碼分析 /C++概觀](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **進階**屬性頁。

1. 修改**設定檔**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>若要設定 Visual Studio 的 CMake 專案內的這個連結器選項

**CMake**專案沒有**屬性頁**，連結器選項可以設定由正在修改的 CMakeLists.txt。

1. 開啟專案根目錄中的 [CMakeLists.txt]。

1. 新增下列程式碼。 如需詳細資訊，請參閱[CMake 參考](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. 重建您的方案。

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)


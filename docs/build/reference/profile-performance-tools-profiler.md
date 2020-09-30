---
title: /PROFILE (效能工具分析工具)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 07952c979fd66291b1744521d83e4556f010d297
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500792"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (效能工具分析工具)

產生可與效能工具分析工具搭配使用的輸出檔。

## <a name="syntax"></a>語法

```
/PROFILE
```

## <a name="remarks"></a>備註

/PROFILE 意指下列連結器選項：

- [/OPT： REF](opt-optimizations.md)

- /OPT： NOICF

- [/INCREMENTAL：否](incremental-link-incrementally.md)

- [/FIXED：否](fixed-fixed-base-address.md)

/PROFILE 會導致連結器產生程式映射中的重新配置區段。  重新配置區段可讓 profiler 轉換程式影像以取得設定檔資料。

**/PROFILE** 僅適用于 Enterprise (team 開發) 版本。  如需 PREfast 的詳細資訊，請參閱 [C/c + + 的程式碼分析總覽](../../code-quality/code-analysis-for-c-cpp-overview.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性]**** 節點。

1. 展開 [連結器]**** 節點。

1. 選取 [進階]**** 屬性頁。

1. 修改 **設定檔** 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>在 Visual Studio CMake 專案中設定這個連結器選項

**CMake** 專案沒有 **屬性頁面**，您可以藉由 modifing CMakeLists.txt 來設定連結器選項。

1. 開啟專案根目錄中的 CMakeLists.txt。

1. 新增下列程式碼。 如需詳細資訊，請參閱 [CMake 參考](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. 重建您的解決方案。

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)

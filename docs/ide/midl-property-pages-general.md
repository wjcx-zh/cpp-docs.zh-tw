---
title: MIDL 屬性頁：一般 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.OVERWRITEStandardIncludePath
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: 0692484c-a7e6-4270-8df7-981589368399
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32e1c743844d252b391a4a747d803ba0e8c81c54
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431420"
---
# <a name="midl-property-pages-general"></a>MIDL 屬性頁：一般

**MIDL** 資料夾中的 [一般] 屬性頁指定下列 MIDL 編譯器選項：

- 前置處理器定義 [(/D](https://msdn.microsoft.com/library/windows/desktop/aa367321))

- 其他 Include 目錄 ([/I](https://msdn.microsoft.com/library/windows/desktop/aa367328))

- 忽略標準 Include 路徑 ([/no_def_idir](https://msdn.microsoft.com/library/windows/desktop/aa367347))

- MkTypLib 相容 ([/mktyplib203](https://msdn.microsoft.com/library/windows/desktop/aa367332))

- 警告層級 ([/W](https://msdn.microsoft.com/library/windows/desktop/aa367383))

- 警告視為錯誤 ([/WX](https://msdn.microsoft.com/library/windows/desktop/aa367387))

- 隱藏程式啟始資訊 ([/nologo](https://msdn.microsoft.com/library/windows/desktop/aa367341))

- MIDL Char 型別 ([/char](https://msdn.microsoft.com/library/windows/desktop/aa367314))

- 目標環境 ([/env](https://msdn.microsoft.com/library/windows/desktop/aa367323))

- 產生 Stubless Proxy ([/Oicf](https://msdn.microsoft.com/library/windows/desktop/aa367352))

如需如何存取 **MIDL** 資料夾中 [一般] 屬性頁的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

如需如何以程式設計方式存取 C++ 專案的 MIDL 選項的資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> 物件。

## <a name="see-also"></a>請參閱

[MIDL 屬性頁](../ide/midl-property-pages.md)
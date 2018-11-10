---
title: MIDL 屬性頁：進階
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
ms.openlocfilehash: 86152dd1ac0bb079a841efa2d27109ee92d48ea7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440868"
---
# <a name="midl-property-pages-advanced"></a>MIDL 屬性頁：進階

**MIDL** 資料夾中的 [進階] 屬性頁指定下列 MIDL 編譯器選項：

- 啟用錯誤檢查 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 檢查配置 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 檢查限制 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 檢查列舉範圍 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 檢查參考指標 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 檢查 Stub 資料 ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- 驗證參數 ([/robust](https://msdn.microsoft.com/library/windows/desktop/aa367363)) \*

- 結構成員對齊 ([/Zp](https://msdn.microsoft.com/library/windows/desktop/aa367388))

- 重新導向輸出 ([/o](https://msdn.microsoft.com/library/windows/desktop/aa367351))

- C 前置處理器選項 ([/cpp_opt](https://msdn.microsoft.com/library/windows/desktop/aa367318))

- 取消前置處理器的定義 ([/U](https://msdn.microsoft.com/library/windows/desktop/aa367373))

\* /robust 只用於針對 Windows 2000 或更新版本的電腦建置時。 如果您建置 ATL 專案，而且想要使用 /robust，請變更 dlldatax.c 檔中的這一行：

```
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM
to
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM
```

如需如何存取 **MIDL** 資料夾中 [進階] 屬性頁的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

如需如何以程式設計方式存取 C++ 專案的 MIDL 選項的資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>。

## <a name="see-also"></a>請參閱

[MIDL 屬性頁](../ide/midl-property-pages.md)
---
title: 專案建置警告 PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191741"
---
# <a name="project-build-warning-prj0049"></a>專案建置警告 PRJ0049

參照的目標 '\<參考 > ' 需要 .NET Framework \<MinFrameworkVersion >，而且將無法在此專案的目標架構上執行

使用 Visual Studio 2008 建立的應用程式可以指定應將哪個版本的 .NET Framework 作為目標。 如果您加入的元件或專案參考相依于目標版本較晚的 .NET Framework 版本，您就會在編譯時期收到這個警告。

### <a name="to-correct-this-warning"></a>更正此警告

1. 選擇下列其中之一：

   - 在專案的 [**屬性頁**] 對話方塊中變更目標架構，使其晚于或等於所有參考元件和專案的最小 framework 版本。 如需詳細資訊，請參閱[加入參考](../../build/adding-references-in-visual-cpp-projects.md)。

   - 移除具有最小架構版本的元件或專案的參考，但其比目標 framework 更晚。 這些專案會在專案的**屬性頁**中標示警告圖示。

## <a name="see-also"></a>另請參閱

[專案建置錯誤和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)

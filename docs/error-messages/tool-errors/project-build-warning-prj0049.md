---
title: 專案建置警告 PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: 0252103757df1c5dc95c9691c6da1d3630d29772
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035555"
---
# <a name="project-build-warning-prj0049"></a>專案建置警告 PRJ0049

參考的目標 '\<參考 >' 需要.NET Framework \<MinFrameworkVersion > 這個專案的目標 framework 執行將會失敗

使用 Visual Studio 2008 建立的應用程式可以指定應該針對.NET Framework 版本。 如果您新增的參考組件或晚於目標版本的.NET framework 的版本而定的專案時，您會在編譯時期這個警告。

### <a name="to-correct-this-warning"></a>若要更正這個警告

1. 選擇下列其中一項：

   - 變更在專案的目標的 framework**屬性頁**對話方塊讓您可晚於或等於最小 framework 版本的所有參考的組件和專案。 如需詳細資訊，請參閱 <<c0> [ 將參考加入](../../build/adding-references-in-visual-cpp-projects.md)。

   - 移除參考的組件或晚於目標 framework 的最小 framework 版本的專案。 這些項目會標示警告圖示，在專案的**屬性頁**。

## <a name="see-also"></a>另請參閱

[專案組建錯誤和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
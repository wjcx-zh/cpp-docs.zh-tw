---
title: ATL 專案精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.atl.com.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- ATL Project Wizard
ms.assetid: 564d2aaf-5b8e-4c2a-a925-ca40a283ea34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7ac74d1b310f4db7bfc4a558db5b89df5d8df5a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109843"
---
# <a name="atl-project-wizard"></a>ATL 專案精靈

Active Template Library (ATL) 是一份樣板架構 c + + 類別，可簡化撰寫小型且快速的 COM 物件。 [ATL 專案精靈] 建立專案結構，以包含 COM 物件。

## <a name="overview"></a>總覽

這個精靈頁面說明目前[ATL 專案的應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)您所建立。 根據預設，專案會有下列設定：

- 動態連結程式庫指定您的伺服器是 DLL，因此同處理序伺服器。

- 您的專案使用屬性的指定屬性化。

若要變更這些預設值，請按一下**應用程式設定**精靈並進行變更的 ATL 專案精靈 頁面中的左資料行中。

如需預設專案設定，包括選擇的字元集，以及連結的預設值，請參閱[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)。

建立 ATL 專案之後，您可以將物件或控制項加入您的專案使用 Visual c + +[程式碼精靈](../../ide/adding-functionality-with-code-wizards-cpp.md)。 您可以進行下列類型的基本的 ATL 專案，使用程式碼精靈的增強功能：

- [將物件和控制項新增至 ATL 專案](../../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

- [ATL 專案中加入新的介面](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)

- [將 COM + 1.0 元件新增至 ATL 專案](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

此外，當您建立和增強的 ATL 專案時，請考慮這些工作：

- [讓 ATL 物件變成無法建立](../../atl/reference/making-an-atl-object-noncreatable.md)

- [最佳化編譯器為 ATL 專案](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

您可以指定專案屬性 (例如[是否以靜態方式連結到 CRT](../../atl/programming-with-atl-and-c-run-time-code.md)) 中[專案屬性](../../ide/general-property-page-project.md)頁面上，而且您可以設定[組建組態](/visualstudio/ide/understanding-build-configurations)的ATL 專案。

## <a name="see-also"></a>另請參閱

[建立和管理 Visual C++ 專案](../../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[Visual C++ 專案類型](../../ide/visual-cpp-project-types.md)<br/>
[使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[教學課程](../../atl/active-template-library-atl-tutorial.md)


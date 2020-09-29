---
title: 新增 ATL 簡單物件
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 85c19c483ff27bd34431ec163e3baadac1855236
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499346"
---
# <a name="adding-an-atl-simple-object"></a>新增 ATL 簡單物件

若要將 ATL (Active Template Library) 物件加入至您的專案，您的專案必須已經建立為 ATL 應用程式，或包含 ATL 支援的 MFC 應用程式。 您可以使用 [ [ATL 專案嚮導]](../../atl/reference/atl-project-wizard.md) 來建立 atl 應用程式，或 [將 atl 物件加入至 mfc 應用](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) 程式，以執行 MFC 應用程式的 atl 支援。

當您第一次建立新的 ATL 物件時，您可以為新的 ATL 物件定義 COM 介面，或稍後使用**類別檢視**快捷方式功能表中的 [[執行介面](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard)] 命令將其加入。

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>將 ATL 簡單物件新增至您的 ATL COM 專案

1. 在 **方案總管** 或 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下您要新增 ATL 簡單物件的專案名稱。

1. 從捷徑功能表按一下 [新增]****，然後按一下 [新增類別]****。

1. 在 [ [加入類別](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) ] 對話方塊的 [ **範本** ] 窗格中，按一下 [ **atl 簡單物件**]，然後按一下 [ **開啟** ] 以顯示 [ATL simple object Wizard](../../atl/reference/atl-simple-object-wizard.md)。

1. 在**ATL Simple Object** wizard 的 [[選項](../../atl/reference/options-atl-simple-object-wizard.md)] 頁面上，為您的專案設定其他選項。

1. 按一下 **[完成]** ，將物件新增至您的專案。

## <a name="see-also"></a>另請參閱

[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[在 ATL 專案中新增介面](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[將連接點加入物件](../../atl/adding-connection-points-to-an-object.md)<br/>
[新增方法](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC 類別](../../mfc/reference/adding-an-mfc-class.md)<br/>
[新增泛型 C++ 類別](../../ide/adding-a-generic-cpp-class.md)

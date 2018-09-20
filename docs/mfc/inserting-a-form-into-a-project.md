---
title: 將表單插入專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83606041250dafed0ef57eb4eea18d7314e0bbef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429262"
---
# <a name="inserting-a-form-into-a-project"></a>將表單插入專案中

表單控制項提供一個便利的容器。 您可以輕鬆地插入 MFC 為基礎的表單應用程式，只要應用程式支援的 MFC 程式庫。

### <a name="to-insert-a-form-into-your-project"></a>若要將表單插入專案

1. 從類別檢視 中，選取您要加入表單的專案並按一下滑鼠右鍵。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入類別**。

     如果**新型**命令無法使用，可以根據您的專案上 Active Template Library (ATL) 中。 若要將表單新增至 ATL 專案中，您必須[指定某些設定](../atl/reference/application-settings-atl-project-wizard.md)首次建立專案時。

1. 從**MFC**資料夾中，按一下**MFC 類別**。

1. 使用 MFC 類別精靈 中，讓新類別衍生自[CFormView](../mfc/reference/cformview-class.md)。

Visual c + + 將表單加入您的應用程式中，開啟對話方塊編輯器內，如此您就可以開始新增控制項和處理其整體設計。

若要執行下列額外的步驟 （不適用於對話方塊架構應用程式）：

1. 覆寫`OnUpdate`成員函式。

1. 實作您的檢視中的資料移至您的文件的成員函式。

1. 建立`OnPrint`成員函式。

## <a name="see-also"></a>另請參閱

[表單檢視](../mfc/form-views-mfc.md)


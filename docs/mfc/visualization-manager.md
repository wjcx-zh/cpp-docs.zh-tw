---
title: 視覺化管理員
ms.date: 11/19/2018
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
ms.openlocfilehash: 9c9dc19266d80d56f696953c5f5896eb9d99cc8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358537"
---
# <a name="visualization-manager"></a>視覺化管理員

視覺管理員時的物件可控制整個應用程式的外觀。 它會將單一類別作為您可以在其中放置您的應用程式的所有繪圖程式碼。 MFC 程式庫包含數個視覺管理員。 如果您想要建立您的應用程式的自訂檢視，您也可以建立您自己的視覺管理員。 啟用不同的視覺管理員時下, 圖將顯示同一個應用程式：

![由 CMFCVisualManagerWindows 呈現的 MyApp](../mfc/media/vmwindows.png "由 CMFCVisualManagerWindows 呈現的 MyApp") <br/>
使用 CMFCVisualManagerWindows 視覺管理員的 MyApp

![由 CMFCVisualManagerVS2005 呈現的 MyApp](../mfc/media/vmvs2005.png "由 CMFCVisualManagerVS2005 呈現的 MyApp") <br/>
使用 CMFCVisualManagerVS2005 視覺管理員的 MyApp

![由 CMFCVisualManagerOfficeXP 呈現的 MyApp](../mfc/media/vmofficexp.png "由 CMFCVisualManagerOfficeXP 呈現的 MyApp") <br/>
使用 CMFCVisualManagerOfficeXP 視覺管理員的 MyApp

![由 CMFCVisualManagerOffice2003 呈現的 MyApp](../mfc/media/vmoffice2003.png "由 CMFCVisualManagerOffice2003 呈現的 MyApp") <br/>
使用 CMFCVisualManagerOffice2003 視覺管理員的 MyApp

![由 CMFCVisualManagerOffice2007 呈現的 MyApp](../mfc/media/msoffice2007.png "由 CMFCVisualManagerOffice2007 呈現的 MyApp") <br/>
使用 CMFCVisualManagerOffice2007 視覺管理員的 MyApp

根據預設，視覺管理員會維護 GUI 的幾個元素的繪製程式碼。 若要提供自訂的 UI 項目，您需要覆寫相關的繪圖方法的視覺管理員。 如需這些方法的清單，請參閱[CMFCVisualManager 類別](../mfc/reference/cmfcvisualmanager-class.md)。 您可以覆寫，以提供自訂外觀的方法為開頭的所有方法`OnDraw`。

您的應用程式只能有一個`CMFCVisualManager`物件。 若要取得 visual 的管理員，您的應用程式的指標，呼叫此靜態函式[CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance)。 因為所有的視覺管理員繼承自`CMFCVisualManager`，則`CMFCVisualManager::GetInstance`方法會取得的指標給適當的視覺管理員，即使您建立自訂的視覺管理員。

如果您想要建立自訂的視覺管理員時，必須先將它衍生自已經存在的視覺管理員。 若要從衍生的預設類別是`CMFCVisualManager`。 不過，您可以使用不同的視覺管理員，如果它更類似於您要為您的應用程式。 例如，如果您想要使用`CMFCVisualManagerOffice2007`視覺化管理員 中，但想要僅適用於變更分隔符號的外觀，您可以衍生自訂類別從`CMFCVisualManagerOffice2007`。 在此案例中，您應該覆寫的方法來繪製分隔符號。

有兩種可能的方式，為您應用程式使用特定的視覺管理員。 其中一種方式是呼叫[cmfcvisualmanager:: Setdefaultmanager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager)方法並傳遞適當的視覺管理員做為參數。 下列程式碼範例示範如何使用`CMFCVisualManagerVS2005`視覺管理員使用這種方法：

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

應用程式中使用的視覺管理員其他辦法是手動建立它。 應用程式再將這個新的視覺管理員用於所有的轉譯。 不過，因為可以只有一個`CMFCVisualManager`物件每個應用程式，您必須先建立一個新刪除目前的視覺管理員。 在下列範例中，`CMyVisualManager`是衍生自的自訂視覺管理員`CMFCVisualManager`。 哪些視覺管理員用來顯示您的應用程式，根據索引時，將下列方法：

```cpp
void CMyApp::SetSkin (int index)
{
    if (CMFCVisualManager::GetInstance() != NULL)
    {
        delete CMFCVisualManager::GetInstance();
    }

    switch (index)
    {
    case DEFAULT_STYLE:
        // The following statement creates a new CMFCVisualManager
        CMFCVisualManager::GetInstance();
        break;

    case CUSTOM_STYLE:
        new CMyVisualManager;
        break;

    default:
        CMFCVisualManager::GetInstance();
        break;
    }

    CMFCVisualManager::GetInstance()->RedrawAll();
}
```

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[CMFCVisualManager 類別](../mfc/reference/cmfcvisualmanager-class.md)

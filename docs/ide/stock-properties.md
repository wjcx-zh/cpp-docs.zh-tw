---
title: 內建屬性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 201e6f0591d446dc0e6b036cfd7ac6f3028eb812
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430258"
---
# <a name="stock-properties"></a>內建屬性

如果您想要使用 [[新增屬性精靈]](../ide/idl-attributes-add-property-wizard.md) 將屬性新增至 MFC 分配介面 (Dispinterface)，您可以在精靈的 [[名稱]](../ide/names-add-property-wizard.md) 頁面中，從 **[屬性名稱]** 清單選擇內建屬性。 這些屬性如下所示：

|屬性名稱|描述|
|-------------------|-----------------|
|**Appearance**|傳回或設定值，這個值可決定控制項的外觀。 控制項的 **Appearance** 屬性可以包含或省略 3D 顯示效果。 這是環境讀取/寫入屬性。|
|`BackColor`|傳回控制項的環境 `BackColor` 屬性，或設定為調色盤 (RGB) 色彩或預先定義的系統色彩。 根據預設，其值會對應至控制項容器的前景色彩。 這是環境讀取/寫入屬性。|
|`BorderStyle`|傳回或設定控制項的框線樣式。 這是讀取/寫入屬性。|
|**標題**|傳回或設定控制項的 **Caption** 屬性。 Caption 是視窗的標題。 **Caption** 沒有**成員變數**實作類型。|
|**已啟用**|傳回或設定控制項的 **Enabled** 屬性。 啟用的控制項可以回應使用者產生的事件。|
|**字型**|傳回或設定控制項的環境字型。 如果控制項沒有字型，則為 Null。|
|`ForeColor`|傳回或設定控制項的環境 `ForeColor` 屬性。|
|**hWnd**|傳回或設定控制項的 **hWnd** 屬性。 **hWnd** 沒有**成員變數**實作類型。|
|**ReadyState**|傳回或設定控制項的 **ReadyState** 屬性。 控制項可以是未初始化、已初始化、正在載入、互動式或完成。 如需詳細資訊，請參閱「網際網路 SDK」中的 [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx)。|
|**Text**|傳回或設定控制項內含的文字。 **Text** 沒有**成員變數**實作類型。|

## <a name="see-also"></a>請參閱

[新增屬性](../ide/adding-a-property-visual-cpp.md)<br>
[新增屬性精靈、IDL 屬性](../ide/idl-attributes-add-property-wizard.md)
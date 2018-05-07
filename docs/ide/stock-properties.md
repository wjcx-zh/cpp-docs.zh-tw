---
title: 內建屬性 |Microsoft 文件
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
ms.openlocfilehash: a3586fb33c30148c870b096d0d49a41d7ad8c6c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="stock-properties"></a>內建屬性
如果您要將屬性加入 MFC dispinterface 使用[加入屬性精靈](../ide/idl-attributes-add-property-wizard.md)，您可以選擇從內建屬性**屬性名稱**清單中[名稱](../ide/names-add-property-wizard.md)頁面精靈。 這些屬性如下所示：  
  
|屬性名稱|描述|  
|-------------------|-----------------|  
|**外觀**|傳回或設定值，這個值會決定控制項的外觀。 控制項的**外觀**屬性可以包含或省略 3d 顯示效果。 這是環境的讀取/寫入屬性。|  
|`BackColor`|傳回或設定控制項的環境`BackColor`調色盤 (RGB) 色彩或預先定義的系統色彩屬性。 根據預設，其值會對應至控制項容器的前景色彩。 這是環境的讀取/寫入屬性。|  
|`BorderStyle`|傳回或設定控制項的框線樣式。 這是讀/寫屬性。|  
|**標題**|傳回或設定控制項的**標題**屬性。 標題是視窗的標題。 **標題**之中未包含任何**成員變數**實作類型。|  
|**已啟用**|傳回或設定控制項的**啟用**屬性。 啟用的控制項可以回應使用者產生的事件。|  
|**字型**|傳回或設定控制項的環境字型。 如果控制項不具有任何字型，則為 null。|  
|`ForeColor`|傳回或設定控制項的環境`ForeColor`屬性。|  
|**hWnd**|傳回或設定控制項的**hWnd**屬性。 **hWnd**之中未包含任何**成員變數**實作類型。|  
|**ReadyState**|傳回或設定控制項的**ReadyState**屬性。 控制項可以是未初始化、 初始化、 載入、 互動式或完成。 請參閱[READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx)中*網際網路 SDK*如需詳細資訊。|  
|**Text**|傳回或設定控制項中包含的文字。 **文字**之中未包含任何**成員變數**實作類型。|  
  
## <a name="see-also"></a>另請參閱  
 [加入屬性](../ide/adding-a-property-visual-cpp.md)   
 [新增屬性精靈、IDL 屬性](../ide/idl-attributes-add-property-wizard.md)
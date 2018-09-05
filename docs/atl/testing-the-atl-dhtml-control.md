---
title: 測試 ATL DHTML 控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls
- DHTML controls, testing
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be4bb44455fb97a61cb4af608667bd5c05f2756a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766288"
---
# <a name="testing-the-atl-dhtml-control"></a>測試 ATL DHTML 控制項

當您建立專案之後時，您可以建置及測試範例控制項。 這麼做之前，請檢查專案中使用類別檢視 和 方案總管 中。 更詳細地描述您的專案項目[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

#### <a name="to-build-and-test-the-atl-dhtml-control"></a>若要建置和測試 ATL DHTML 控制項

1. 建置專案。 從**建置**功能表上，按一下**建置方案**。

2. 當組建完成時，請開啟 測試容器。 請參閱[以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如需有關如何測試容器存取資訊。

3. 在測試容器中，從**編輯**功能表上，按一下**插入新控制項**。

4. 在 **插入控制項**對話方塊方塊中，從清單方塊中選取您的控制項。 請記住，其名稱根據您在 ATL 控制項精靈中指示的簡短名稱。 按一下 [確定 **Deploying Office Solutions**]。

5. 檢查控制項。 請注意，它會有捲軸。 您可以使用控制項的控點來調整啟用捲軸控制項的大小。

6. 測試控制項的按鈕。 背景色彩變更為以按鈕的色彩。

7. 關閉測試容器。

接下來請嘗試[修改 DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)。

## <a name="see-also"></a>另請參閱

[DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)


---
title: 如何： 開啟 c + + 專案 （獨立式） 外的資源指令碼檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e52d78de0026fa4a589877ee0a591da26107fde
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391527"
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>如何： 開啟 c + + 專案 （獨立式） 外的資源指令碼檔案

您可以檢視 .rc 檔中的資源，而不需要開啟一個專案。 .Rc 檔會在相對於在文件視窗中開啟[資源檢視](../windows/resource-view-window.md)視窗 （如同在專案內開啟檔案時）。

> [!NOTE]
> 這是一項重要的差異，因為某些命令只有在獨立開啟檔案時 (在專案外)，才可供使用。 比方說，您可以只將檔案儲存在不同的格式或不同的檔案名稱在專案外開啟檔案時 (**另存新檔**專案內開啟的檔案時，命令便無法使用)。

### <a name="to-open-an-rc-file-outside-a-project"></a>開啟專案外部的 .rc 檔案

1. 從**檔案**功能表上，選擇**開放**，然後按一下**檔案**。

2. 在 **開啟的檔案**對話方塊方塊中，瀏覽至您想要檢視、 反白顯示檔案，然後按一下資源指令碼檔**開啟**。

   > [!NOTE]
   > 如果您第一次開啟專案 (**檔案**，**開啟**，**專案**)，有些命令不會提供給您。 「獨立」開啟檔案表示開啟檔案而不先載入專案。

若要開啟並檢視文字格式的資源檔，請參閱[編輯資源指令碼 (.rc) 檔](../windows/how-to-open-a-resource-script-file-in-text-format.md)。

### <a name="to-open-multiple-rc-files-outside-a-project"></a>開啟專案外的多個 .rc 檔

1. 開啟兩個獨立資源檔案。 例如，開啟`Source1.rc`和`Source2.rc`。

   1. 從**檔案**功能表上，選擇**開放**，然後按一下**檔案**。

   2. 在 **開啟的檔案**對話方塊方塊中，巡覽至您想要開啟的第一個資源指令碼檔案 (`Source1.rc`)，反白顯示檔案，然後按一下**開啟**。

   3. 重複上述步驟來開啟第二個.rc 檔餇 (`Source2.rc`)。

       .rc 檔現在會在個別的文件視窗中開啟。

2. 開啟兩個 .rc 檔時，並排顯示視窗，以讓您同時檢視：

   - 從** 視窗**功能表上，選擇**新增水平索引標籤群組**或是**新增垂直索引標籤群組**。

       \-或-

   - 以滑鼠右鍵按一下其中一個.rc 檔，然後選擇 **新增的水平索引標籤群組**或是**新增垂直索引標籤群組**從捷徑功能表。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)
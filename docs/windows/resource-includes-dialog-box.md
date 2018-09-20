---
title: 資源包含對話方塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourceincludes
dev_langs:
- C++
helpviewer_keywords:
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 626327fec8efda873551e6d9ee502d7405eec5a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371975"
---
# <a name="resource-includes-dialog-box-c"></a>資源包含對話方塊 （c + +）

您可以使用**Resource Includes**對話方塊中，在 c + + 專案中，修改儲存專案.rc 檔和所有中的所有資源的環境的一般工作安排[符號](../windows/symbols-resource-identifiers.md)Resource.h 中。

若要開啟 [ **Resource Includes** ] 對話方塊中，以滑鼠右鍵按一下.rc 檔案中[資源檢視](../windows/resource-view-window.md)，然後選擇**Resource Includes**從捷徑功能表。

- **符號標頭檔**

   可讓您變更標頭檔的名稱，您的資源的符號定義就是儲存在這個標頭檔中。 如需詳細資訊，請參閱 <<c0> [ 變更符號標頭檔的名稱](../windows/changing-the-names-of-symbol-header-files.md)。

- **唯讀符號指示詞**

   可讓您包含標頭檔，其中包含編輯工作階段期間不應該修改的符號。 例如，您可以包含數個專案之間共用的符號檔案。 您也可以包含 MFC.h 檔案。 如需詳細資訊，請參閱 <<c0> [ 包含共用 （唯讀） 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)。

- **編譯時間指示詞**

   可讓您包含從您的主要資源檔中資源個別建立和編輯的資源檔、包含編譯時間指示詞 (例如，有條件地包含資源的編譯時間指示詞)，或包含自訂格式的資源。 您也可以使用**編譯時間指示詞方塊**包含標準 MFC 資源檔。 如需詳細資訊，請參閱 <<c0> [ 在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。

> [!NOTE]
> 這些文字方塊中的項目剢謅.rc 檔餇標示`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分別。 如需詳細資訊，請參閱 < [TN035： 使用多個資源檔和 Visual c + + 的標頭檔](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

一旦您已使用資源檔案變更**Resource Includes**  對話方塊中，您需要關閉.rc 檔案，然後再重新開啟，讓變更生效。 如需詳細資訊，請參閱 <<c0> [ 在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：指定資源的 Include 目錄](../windows/how-to-specify-include-directories-for-resources.md)<br/>
[符號：資源識別項](../windows/symbols-resource-identifiers.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)
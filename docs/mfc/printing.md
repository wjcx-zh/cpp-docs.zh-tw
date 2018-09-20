---
title: 列印 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e03e750941be02385ac4d5b7463d5b6f32997b6a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373944"
---
# <a name="printing"></a>列印

Microsoft Windows 中，會實作與裝置無關的顯示。 在 MFC 中，這表示相同的繪製呼叫，在`OnDraw`您的檢視類別成員函式會負責顯示和其他裝置，例如印表機上的繪圖。 預覽列印，目標裝置是模擬的印表機輸出到顯示器。

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> 您在列印與架構的角色中的角色

您的檢視類別具有下列責任：

- 告知架構文件中有多少頁數。

- 當要求列印指定的頁面，請繪製文件的部分。

- 配置及取消配置任何字型或其他列印所需的圖形裝置介面 (GDI) 資源。

- 如有必要，傳送任何逸出程式碼所需變更印表機模式，再列印特定的頁面，例如，若要變更每個頁面為基礎的列印方向。

架構的責任如下所示：

- 顯示**列印** 對話方塊。

- 建立[CDC](../mfc/reference/cdc-class.md)印表機的物件。

- 呼叫[StartDoc](../mfc/reference/cdc-class.md#startdoc)並[EndDoc](../mfc/reference/cdc-class.md#enddoc)的成員函式`CDC`物件。

- 重複呼叫[StartPage](../mfc/reference/cdc-class.md#startpage)成員函式`CDC`物件，告知哪些頁面應該會印出，並呼叫的檢視類別[EndPage](../mfc/reference/cdc-class.md#endpage)成員函式`CDC`物件。

- 呼叫可覆寫的函式在檢視中，在適當的時間。

下列文章將討論如何架構支援列印和預覽列印：

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [如何完成預設列印](../mfc/how-default-printing-is-done.md)

- [多頁文件](../mfc/multipage-documents.md)

- [頁首和頁尾](../mfc/headers-and-footers.md)

- [列印配置 GDI 資源](../mfc/allocating-gdi-resources.md)

- [預覽列印](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>另請參閱

[列印和預覽列印](../mfc/printing-and-print-preview.md)


---
title: 功能表命令屬性 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c846cecb415365db92e3097bbf04ab06cd4209d0
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860442"
---
# <a name="menu-command-properties-c"></a>功能表命令屬性 （c + +）

下列資訊會根據組織** 功能表**屬性中出現[屬性 視窗](/visualstudio/ide/reference/properties-window)當您選取功能表命令。 這些字母順序列出雖然**屬性**視窗也可讓您依類別檢視這些屬性。

|屬性|描述|
|--------------|-----------------|
|**Break**|可以是下列值之一：<br /><br />- **無**（預設）： 不換行。<br />- **資料行**： 對於靜態功能表，這個值會將功能表命令放在新行上。 對於快顯功能表，這個值會將功能表命令放在資料行中，而且資料行之間沒有分隔線。 設定這個屬性只會在執行階段影響功能表的外觀，但在功能表編輯器中卻不會。<br />- **橫條**： 與相同**資料行**除了針對快顯功能表，這個值會區隔新的資料行從舊的資料行，以垂直線。 設定這個屬性會影響功能表的外觀，只有在執行階段，不是在** 功能表**編輯器。|
|**標題**|標示功能表命令的文字 (功能表名稱)。 若要讓功能表命令的其中一個大寫字母成為助憶鍵，請在其前面加下連字號 (&)。|
|**已核取**|如果 **，則為 True**，功能表命令一開始選取。 類型： **Bool**。 預設值： **False**。|
|**已啟用**|若為 **False**，則會停用功能表項目。|
|**呈現灰色**|如果 **，則為 True**，功能表命令是一開始呈現灰色，而且非使用中。 類型： **Bool**。 預設值： **False**。|
|**說明**|將功能表項目對齊右邊。 例如，[ **說明** ] 功能表命令一律在所有 Windows 應用程式的右邊。 如果您在功能表項目上設定這個屬性，該項目將出現在功能表的最右邊和最尾端。 適用於最上層項目。 預設值： **False**。|
|**ID**|定義在標頭中的符號。 類型：**符號**，**整數**，或**加引號的字串**。 您可以使用任何通常可在任何編輯器使用的符號，即使 [屬性視窗](/visualstudio/ide/reference/properties-window) 未提供可讓您從中選取的下拉式清單也一樣。|
|**快顯**|如果 **，則為 True**，功能表命令是快顯功能表。 類型： **Bool**。 預設值：**真**最上層功能表的功能表列; 否則為**False**。|
|**提示**|包含反白顯示此功能表命令時要出現在狀態列的文字。 文字會放在字串表中，其識別碼與功能表命令相同。 這個屬性適用於任何類型的專案，但執行階段功能則專屬於 MFC。|
|**由右至左對齊**|在執行階段將功能表列上的功能表命令靠右對齊。 類型： **Bool**。 預設值： **False**。|
|**順序由右至左**|當介面當地語系化為任何由右至左讀取的語言 (例如希伯來文或阿拉伯文) 時，可讓功能表命令由右至左顯示。|
|**Separator**|如果 **，則為 True**，功能表命令為分隔符號。 類型： **Bool**。 預設值： **False**。|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)
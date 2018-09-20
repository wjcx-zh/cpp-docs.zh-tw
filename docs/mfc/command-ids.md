---
title: 命令 Id |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5087c271151793169cbf7350f78750044ccead0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446968"
---
# <a name="command-ids"></a>命令 ID

命令的完整說明所單獨其命令識別碼 (編碼**WM_COMMAND**訊息)。 此識別碼被指派給產生命令的使用者介面物件。 一般而言，識別碼會命名為它們指派給使用者介面物件的功能。

比方說，在 編輯 功能表中的 全部清除項目可能會指派識別碼這類**ID_EDIT_CLEAR_ALL**。 類別庫預先定義的部分識別碼，特別是針對命令，架構會處理本身，例如**ID_EDIT_CLEAR_ALL**或是**ID_FILE_OPEN**。 您將會自行建立其他的命令 Id。

當您建立您自己的功能表中 Visual c + + 功能表編輯器時，它是個不錯的主意，請依照下列類別庫的命名慣例，如下圖所示**ID_FILE_OPEN**。 [標準命令](../mfc/standard-commands.md)說明標準類別程式庫所定義的命令。

## <a name="see-also"></a>另請參閱

[使用者介面物件和命令識別碼](../mfc/user-interface-objects-and-command-ids.md)


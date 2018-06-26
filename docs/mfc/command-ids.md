---
title: 命令 Id |Microsoft 文件
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
ms.openlocfilehash: e1e03f10199c1b582a1a8603a6ea6c93e1d55473
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931228"
---
# <a name="command-ids"></a>命令 ID
命令的完整說明單獨命令識別碼 (以編碼**WM_COMMAND**訊息)。 這個識別碼被指派給產生命令的使用者介面物件。 一般而言，識別碼是名為它們指派給使用者介面物件的功能。  
  
 例如，[編輯] 功能表中的清除所有項目可能會指派識別碼例如**ID_EDIT_CLEAR_ALL**。 類別庫預先定義的部分，特別是命令 Id，架構會處理本身，例如**ID_EDIT_CLEAR_ALL**或**ID_FILE_OPEN**。 您將自己建立其他的命令 Id。  
  
 當您建立您自己的功能表中 Visual c + + 功能表編輯器時，它是個不錯的主意，請依照下列類別庫的命名慣例，如下所示**ID_FILE_OPEN**。 [標準命令](../mfc/standard-commands.md)說明類別庫所定義的標準命令。  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面物件和命令識別碼](../mfc/user-interface-objects-and-command-ids.md)


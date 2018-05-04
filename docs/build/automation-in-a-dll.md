---
title: DLL 中的 automation |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41c5f31a72cf734296ecb281e0785d415c8043a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="automation-in-a-dll"></a>DLL 中的 Automation
當您選擇的 Automation 選項在 MFC DLL 精靈時，精靈會讓您獲得下列：  
  
-   起始物件描述語言 (。ODL) 檔案  
  
-   Include 指示詞 Afxole.h 的 STDAFX.h 檔案中  
  
-   實作`DllGetClassObject`函式，呼叫**AfxDllGetClassObject**函式  
  
-   實作`DllCanUnloadNow`函式，呼叫**AfxDllCanUnloadNow**函式  
  
-   實作`DllRegisterServer`函式，呼叫[COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)函式  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [Automation 伺服程式](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)
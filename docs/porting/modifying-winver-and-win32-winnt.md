---
title: "修改 WINVER 和 _WIN32_WINNT | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_WIN32_WINNT in an upgraded Visual C++ project"
  - "WINVER in an upgraded Visual C++ project"
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 修改 WINVER 和 _WIN32_WINNT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 不再支援將 Windows 95、Windows 98、Windows ME、Windows NT 或 Windows 2000 當做目標。 如果您的 **WINVER** 或 **\_WIN32\_WINNT** 巨集指派給其中一個這些 Windows 版本中，您必須修改巨集。 當您升級使用較早版本的 Visual C\+\+ 所建立的專案時，可能會看到與 **WINVER** 或 **\_WIN32\_WINNT** 巨集相關的編譯錯誤 \(如果它們指派給已不再支援的 Windows 版本\)。  
  
## 備註  
 若要修改巨集，請在標頭檔 \(例如在建立使用 Windows 的專案時會包含 targetver.h\) 中新增下列程式行。  
  
```  
#define WINVER 0x0A00 #define _WIN32_WINNT 0x0A00  
```  
  
 此動作鎖定 Windows 10 作業系統。 這些值會列於 Windows 標頭檔 SDKDDKVer.h，其亦會定義每個 Windows 版本的巨集。 包含 SDKDDKVer.h 前應先新增 \#define 陳述式。 以下是來自 Windows 10 版本 SDKDDKVer.h 的程式行，其會針對每個版本的 Windows 編碼值：  
  
```  
// // _WIN32_WINNT version constants // #define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0 #define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000 #define _WIN32_WINNT_WINXP                  0x0501 // Windows XP #define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003 #define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista #define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista #define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008 #define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista #define _WIN32_WINNT_WIN7                   0x0601 // Windows 7 #define _WIN32_WINNT_WIN8                   0x0602 // Windows 8 #define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1 #define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10 #define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10  
```  
  
 若您發現目前查看的 SDKDDKVer.h 複本未列出所有的 Windows 版本，表示您可能使用舊版的 Windows SDK。 根據預設，[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中的 Win32 專案使用 Windows 8.1 SDK。 若要使用 Windows 10 SDK，請參閱 [如何：在 Windows 桌面應用程式中使用 Windows 10 SDK ](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)。  
  
> [!NOTE]
>  如果您在應用程式中包含內部 MFC 標頭，則不保證值能夠運作。  
  
 您也可以利用 **\/D** 編譯器選項，定義此巨集。 如需詳細資訊，請參閱[\/D \(前置處理器定義\)](../build/reference/d-preprocessor-definitions.md)。  
  
 如需這些巨集的意義的相關資訊，請參閱[使用 Windows 標頭](http://msdn.microsoft.com/library/windows/desktop/aa383745)。  
  
## 請參閱  
 [先前的產品變更](http://msdn.microsoft.com/zh-tw/91fa1713-0778-4b6b-82f7-0fe0a23ab1db)
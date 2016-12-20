---
title: "應用程式和執行緒支援類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.support"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式物件 [C++], 執行緒支援類別"
  - "應用程式支援類別 [C++]"
  - "鎖定類別"
  - "同步類別, 多執行緒"
  - "執行緒支援類別 [C++]"
  - "執行緒 [MFC]"
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式和執行緒支援類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個應用程式只能有一個應用程式物件；這個物件協調執行程式的其他物件並且是衍生自 `CWinApp`。  
  
 執行 Microsoft Foundation Class \(MFC\) 程式庫在應用程式中支援多執行緒。  所有應用程式都必須至少有一個執行緒；`CWinApp` 物件所使用的執行緒是主要執行緒。  
  
 `CWinThread` 封裝作業系統執行緒的功能的一部分。  若要讓使用多執行緒更容易， MFC 也提供同步物件類別，以提供 C \+\+. 介面給 Win32 同步處理物件。  
  
## 應用程式和執行緒類別  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 封裝程式碼，執行初始化和終止應用程式。  您從這個類別會取得您的應用程式物件。  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 所有執行緒的基底類別。  如果您的執行緒執行使用者介面函式，請使用直接或衍生自 `CWinThread` 類別。  `CWinApp` 是衍生自 `CWinThread`。  
  
## 同步物件類別  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 同步物件類別的基底類別。  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 只允許在單一處理序中的執行緒存取物件的同步處理類別。  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 一個同步處理類別，允許對一個項目進行一個指定的最大數目的同時存取。  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 只允許在某些數目的處理序的一個執行緒存取物件的同步處理類別。  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 在發生事件時通知應用程式的同步處理類別。  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 用於安全執行緒類別的成員函式，以鎖定同步物件。  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 用於安全執行緒的成員函式，以在同步物件的陣列中鎖定一或多個同步物件。  
  
## 相關類別  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 解析程式啟動的命令列。  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 在螢幕上放置等候游標。  使用在冗長作業期間。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 處理控制列的停駐狀態資料之永續儲存。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 維護最近使用的 \(MRU\) 檔案清單。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)
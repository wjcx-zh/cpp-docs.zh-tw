---
title: CFtpFileFind 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
dev_langs:
- C++
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88e6916056f988a1cee52020c8ce7e9fce11e574
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cftpfilefind-class"></a>CFtpFileFind 類別
協助 FTP 伺服器的網際網路檔案搜尋。  
  
## <a name="syntax"></a>語法  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|建構 `CFtpFileFind` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cftpfilefind:: Findfile](#findfile)|尋找 FTP 伺服器上的檔案。|  
|[Cftpfilefind:: Findnextfile](#findnextfile)|會繼續從先前呼叫檔案搜尋[FindFile](#findfile)。|  
|[CFtpFileFind::GetFileURL](#getfileurl)|取得 URL，包括找到的檔案路徑。|  
  
## <a name="remarks"></a>備註  
 `CFtpFileFind` 包含 開始搜尋，找出檔案，並傳回 URL 或檔案的其他描述性資訊的成員函式。  
  
 設計網際網路和搜尋的本機檔案包含其他 MFC 類別[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 搭配`CFtpFileFind`，這些類別會提供無縫式的機制，來尋找特定的檔案，不論伺服器通訊協定或檔案類型 （本機電腦或遠端伺服器） 用戶端。 請注意，搜尋在 HTTP 伺服器上，HTTP 不支援所需的搜尋直接在檔案操作作業，因為沒有 MFC 類別。  
  
 如需有關如何使用`CFtpFileFind`和其他 WinInet 類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會示範如何列舉 FTP 伺服器的目前目錄中的所有檔案。  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind  
 呼叫此成員函式會建構`CFtpFileFind`物件。  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `pConnection`  
 指標`CFtpConnection`物件。 您可以藉由呼叫取得 FTP 連接[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)。  
  
 `dwContext`  
 內容識別項`CFtpFileFind`物件。 請參閱**備註**如需有關此參數。  
  
### <a name="remarks"></a>備註  
 預設值為`dwContext`MFC 所傳送的`CFtpFileFind`物件從[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CFtpFileFind`物件。 您可以覆寫預設值，您選擇的值來設定內容識別碼。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供其所識別的物件上的狀態。 請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
### <a name="example"></a>範例  
  請參閱本主題稍早類別概觀中的範例。  
  
##  <a name="findfile"></a>  Cftpfilefind:: Findfile  
 呼叫此成員函式可尋找 FTP 檔案。  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>參數  
 `pstrName`  
 包含要尋找的檔案名稱的字串指標。 如果**NULL**，呼叫將會搜尋萬用字元 （*）。  
  
 `dwFlags`  
 描述如何處理此工作階段旗標。 可以與位元 OR 運算子結合這些旗標 (&#124;)，如下：  
  
-   INTERNET_FLAG_RELOAD 從線上取得資料，即使在本機快取。 這是預設旗標。  
  
-   INTERNET_FLAG_DONT_CACHE 不會快取資料，在本機或任何閘道。  
  
-   INTERNET_FLAG_RAW_DATA 覆寫預設值，傳回未經處理資料 ( [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) ftp 結構)。  
  
-   使用安全通訊端層或 PCT 網路上的 INTERNET_FLAG_SECURE 保護交易 這個旗標適用於只使用 HTTP 要求。  
  
-   INTERNET_FLAG_EXISTING_CONNECT 如果可能的話，請重複使用現有的連接到伺服器對於新**FindFile**要求，而非建立新的工作階段，針對每個要求。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 若要取得延伸錯誤資訊，請呼叫 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>備註  
 在呼叫**FindFile**擷取第一個 FTP 檔案，您可以呼叫[FindNextFile](#findnextfile)擷取後續 FTP 檔案。  
  
### <a name="example"></a>範例  
  請參閱本主題中較早的範例。  
  
##  <a name="findnextfile"></a>  Cftpfilefind:: Findnextfile  
 呼叫此成員函式，繼續呼叫開始檔案搜尋[FindFile](#findfile)成員函式。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果有多個檔案。如果找到該檔案的目錄中的最後一個，或發生錯誤，則為零。 若要取得延伸錯誤資訊，請呼叫 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到該檔案會在目錄中，最後一個檔案，或如果沒有相符的檔案可以找到`GetLastError`函式會傳回 ERROR_NO_MORE_FILES。  
  
### <a name="remarks"></a>備註  
 您必須至少一次呼叫任何屬性函式之前呼叫此函式 (請參閱[CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile))。  
  
 `FindNextFile` 包裝的 Win32 函式[FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428)。  
  
### <a name="example"></a>範例  
  請參閱本主題稍早的範例。  
  
##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL  
 呼叫此成員函式可取得指定之檔案的 URL。  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案和路徑的通用資源定位器 (URL)。  
  
### <a name="remarks"></a>備註  
 `GetFileURL` 成員函式類似[CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)，不同之處在於它的形式傳回 URL `ftp://moose/dir/file.txt`。  
  
## <a name="see-also"></a>另請參閱  
 [CFileFind 類別](../../mfc/reference/cfilefind-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 類別](../../mfc/reference/chttpfile-class.md)

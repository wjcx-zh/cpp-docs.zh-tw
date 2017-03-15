---
title: "errno 常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENOEXEC"
  - "ENOMEM"
  - "E2BIG"
  - "STRUNCATE"
  - "ENOENT"
  - "EMFILE"
  - "EBADF"
  - "EDEADLOCK"
  - "EXDEV"
  - "EILSEQ"
  - "EINVAL"
  - "EDOM"
  - "EACCES"
  - "ERANGE"
  - "ENOSPC"
  - "EAGAIN"
  - "EEXIST"
  - "ECHILD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "E2BIG 常數"
  - "EACCES 常數"
  - "EAGAIN 常數"
  - "EBADF 常數"
  - "ECHILD 常數"
  - "EDEADLOCK 常數"
  - "EDOM 常數"
  - "EEXIST 常數"
  - "EILSEQ 常數"
  - "EINVAL 常數"
  - "EMFILE 常數"
  - "ENOENT 常數"
  - "ENOEXEC 常數"
  - "ENOMEM 常數"
  - "ENOSPC 常數"
  - "ERANGE 常數"
  - "errno 常數"
  - "EXDEV 常數"
  - "STRUNCATE 常數"
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# errno 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <errno.h>  
```  
  
## 備註  
 **errno** 值是常數在各種錯誤狀況的事件中指派給 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)的 。  
  
 ERRNO.H 包含 **errno** 值的定義。  不過，不是所有在 ERRNO.H 的定義都是給 32 位元 Windows 作業系統使用的。  某些在 ERRNO.H 的值存在維護與作業系統 UNIX 系列的相容性。  
  
 在 32 位元 Windows 作業系統的 **errno** 值是XENIX 系統中**errno**的子集 。  因此， **errno** 值不一定和Windows 作業系統的系統呼叫回傳的實際錯誤碼相同。  若要存取實際作業系統錯誤碼，請使用包含此值的 [\_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 變數。  
  
 支援下列 **errno** 值：  
  
 **ECHILD**  
 沒有產生的處理序。  
  
 **EAGAIN**  
 沒有流程。  嘗試建立新的處理序失敗，因為沒有處理位置或沒有足夠的記憶體，或是最高巢狀層次結尾。  
  
 **E2BIG**  
 引數清單太長。  
  
 **EACCES**  
 使用權限遭拒。  檔案的使用權限設定不允許指定的權限。  這個錯誤表示嘗試存取檔案 \(或是存取目錄\) 是與文件屬性不相容的方法。  
  
 例如，當嘗試從不開啟時的檔案讀取，開啟撰寫的現有唯讀檔案，或開啟目錄而不是檔案時，可能會發生錯誤。  在 MS\-DOS 作業系統版本 3.0 和以後， **EACCES** 也可能表示鎖定或共用違規。  
  
 錯誤也會發生為指定檔案或目錄重新命名或移除現有的目錄。  
  
 **EBADF**  
 錯誤的檔案編號。  有兩個原因: 1\) 指定的檔案描述項不是有效值也無法開啟檔案。2\) 嘗試將開啟的檔案或裝置撰寫成唯讀存取。  
  
 **EDEADLOCK**  
 會發生資源死結。  對數學函式的引數不是函式的定義域。  
  
 **EDOM**  
 算術引數。  
  
 **EEXIST**  
 檔案存在。  嘗試建立已經存在的檔案。  例如， **\_O\_CREAT** 和 **\_O\_EXCL** 旗標在 **\_open** 呼叫指定，不過具此名檔案已經存在。  
  
 **EILSEQ**  
 不合法的位元組序列 \(例如，在 MBCS 字串\)。  
  
 **EINVAL**  
 無效的引數。  無效值為其中一個給所指定函式的引數。  例如，當置放檔案指標時\(傳遞至 **fseek**的呼叫\)給原點的值是在檔案的開頭之前。  
  
 **EMFILE**  
 太多開啟的檔案。  沒有可用的檔案描述項，因此，無法開啟其他檔案。  
  
 **ENOENT**  
 沒有這類檔案或目錄。  指定的檔案或目錄不存在或找不到。  每當至指定的檔案不存在或路徑的元件不指定現有的目錄時，這個訊息可能發生。  
  
 **ENOEXEC**  
 Exec 格式錯誤。  嘗試執行不可執行檔或具有無效的可執行檔格式的檔案。  
  
 **ENOMEM**  
 不夠核心。  沒有足夠的記憶體以嘗試的運算子是可用的。  例如，當沒有足夠的記憶體可用執行子處理序時，或當**\_getcwd** 的設定無法滿足該要求時，可能會發生這個訊息。  
  
 **ENOSPC**  
 沒有在裝置留下任何空間。  裝置已沒有任何空間供寫入 \(例如，磁碟已滿\)。  
  
 **ERANGE**  
 結果太大。  對數學函式的引數太大，造成部分或完整顯著性位元會遺失結果的。  這個錯誤發生於其他函式，也可能會發生在引數比預期大時 \(例如，**\_getcwd** 的引數 超出預期的*緩衝區* 長度\)。  
  
 **EXDEV**  
 跨裝置的連結。  嘗試將檔案移到不同的裝置 \(使用 **rename** 函式\)。  
  
 **STRUNCATE**  
 字串複製或串連造成截斷的字串。  請參閱 [\_TRUNCATE](../c-runtime-library/truncate.md)。  
  
 下列值為與 Posix 的相容性支援。  它們是在非 Posix 系統需要的值。  
  
```  
#define E2BIG [argument list too long]  
#define EACCES [permission denied]  
#define EADDRINUSE [address in use]  
#define EADDRNOTAVAIL [address not available]  
#define EAFNOSUPPORT [address family not supported]  
#define EAGAIN [resource unavailable try again]  
#define EALREADY [connection already in progress]  
#define EBADF [bad file descriptor]  
#define EBADMSG [bad message]  
#define EBUSY [device or resource busy]  
#define ECANCELED [operation canceled]  
#define ECHILD [no child process]  
#define ECONNABORTED [connection aborted]  
#define ECONNREFUSED [connection refused]  
#define ECONNRESET [connection reset]  
#define EDEADLK [resource deadlock would occur]  
#define EDESTADDRREQ [destination address required]  
#define EDOM [argument out of domain]  
#define EEXIST [file exists]  
#define EFAULT [bad address]  
#define EFBIG [file too large]  
#define EHOSTUNREACH [host unreachable]  
#define EIDRM [identifier removed]  
#define EILSEQ [illegal byte sequence]  
#define EINPROGRESS [operation in progress]  
#define EINTR [interrupted]  
#define EINVAL [invalid argument]  
#define EIO [io error]  
#define EISCONN [already connected]  
#define EISDIR [is a directory]  
#define ELOOP [too many synbolic link levels]  
#define EMFILE [too many files open]  
#define EMLINK [too many links]  
#define EMSGSIZE [message size]  
#define ENAMETOOLONG [filename too long]  
#define ENETDOWN [network down]  
#define ENETRESET [network reset]  
#define ENETUNREACH [network unreachable]  
#define ENFILE [too many files open in system]  
#define ENOBUFS [no buffer space]  
#define ENODATA [no message available]  
#define ENODEV [no such device]  
#define ENOENT [no such file or directory]  
#define ENOEXEC [executable format error]  
#define ENOLCK [no lock available]  
#define ENOLINK [no link]  
#define ENOMEM [not enough memory]  
#define ENOMSG [no message]  
#define ENOPROTOOPT [no protocol option]  
#define ENOSPC [no space on device]  
#define ENOSR [no stream resources]  
#define ENOSTR [not a stream]  
#define ENOSYS [function not supported]  
#define ENOTCONN [not connected]  
#define ENOTDIR [not a directory]  
#define ENOTEMPTY [directory not empty]  
#define ENOTRECOVERABLE [state not recoverable]  
#define ENOTSOCK [not a socket]  
#define ENOTSUP [not supported]  
#define ENOTTY [inappropriate io control operation]  
#define ENXIO [no such device or address]  
#define EOPNOTSUPP [operation not supported]  
#define EOTHER [other]  
#define EOVERFLOW [value too large]  
#define EOWNERDEAD [owner dead]  
#define EPERM [operation not permitted]  
#define EPIPE [broken pipe]  
#define EPROTO [protocol error]  
#define EPROTONOSUPPORT [protocol not supported]  
#define EPROTOTYPE [wrong protocol type]  
#define ERANGE [result out of range]  
#define EROFS [read only file system]  
#define ESPIPE [invalid seek]  
#define ESRCH [no such process]  
#define ETIME [stream timeout]  
#define ETIMEDOUT [timed out]  
#define ETXTBSY [text file busy]  
#define EWOULDBLOCK [operation would block]  
#define EXDEV [cross device link]  
```  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)
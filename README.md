# TCPNameToIP
$Net_Result[3] Local $NetAdrs[5] = ["localhost", @ComputerName, "127.0.0.1", "www.google.com", "216.34.181.60"] For $i = 0 To UBound($NetAdrs) - 1     $Net_Result = _mLookup($NetAdrs[$i])     ConsoleWrite($Net_Result[0] &amp; @TAB &amp; $Net_Result[1] &amp; @CRLF) Next    ; This Function accepts either an IPaddress or a Host/Domain name and returns ; a 3 elements array element[0]=IPaddress element[1]=hostname.domain element[2]=hostnameOnly Func _mLookup($Net_ID)     Local $Net_Names[3]     TCPStartup()     If StringRegExp($Net_ID, "^(?:[0-9]{1,3}\.){3}[0-9]{1,3}$") Then         $Net_Names[1] = _TCPIpToName($Net_ID) ; Resolves IP adress to Hostname         If @error Then $Net_Names[1] = "Hostname_error"         $Net_Names[0] = $Net_ID     Else         $Net_Names[0] = TCPNameToIP($Net_ID) ; Resolves Hostname to IP adress

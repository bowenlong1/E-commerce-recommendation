
Sub Checkboxes_s3()
    Dim ws As Worksheet
    Dim cb As CheckBox
    Dim i As Integer
    Dim cellWidth As Double
    Dim cellHeight As Double
    
    ' Set the worksheet
    Set ws = ThisWorkbook.Sheets("v3")
    
    ' Loop through the checkboxes
    For i = 4 To 93 ' Adjust the range as needed
        ' Set position for each checkbox at the center of the cell
        cellWidth = ws.Cells(i, 8).Width
        cellHeight = ws.Cells(i, 8).Height
        
        ' Create checkboxes in columns J to O
        For j = 0 To 2
            Set cb = ws.Checkboxes.Add(ws.Cells(i, 8 + j).Left + (cellWidth - 50) / 2, ws.Cells(i, 8 + j).Top + (cellHeight - 20) / 2, 50, 20)
            
            ' Link each checkbox to the corresponding cell in columns J to O
            cb.LinkedCell = ws.Cells(i, 8 + j).Address
            
            ' Customize checkbox appearance
            cb.Text = "" ' Remove default text
        Next j
    Next i
End Sub

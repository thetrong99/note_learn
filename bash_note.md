compare
    <  or -lt    
    <= or -le    
    >  or -gt
    >= or -ge
    == or -eq
    -ne     khong bang

Cac varible dac biet 

ky tu $ dai dien cho PID
    $0  ten cua tap lenh hien tai
    $n ung voi doi so ma tap lenh duoc goi (n la vi tri doi so)
    $# so luong doi so duoc cung cap cho mot tap lenh
    $* tat ca cac doi so duoc trich dan gap doi
    $@ tat ca cac doi so duoc trich dan rieng le
    $? trang thai thoat cua lenh cuoi cung duoc thuc thi
    $! so tien trinh cua lenh nen cuoi cung
if condition
then
  command
elif
  anothercommand
else
  yetanothercommand
fi 
#cau dieu kien
while condition
do
  command
done
#vong lap while
until condition
do
  command
done
#vong lap until   

for item in list
do
  command
done
#vong lap for

#cau truc case in bash shell
case value in
  a)
    command
    #...
    ;;
  b)
    command
    #...
    ;;
esac
Chúng ta cần thêm một dấu chấm phẩy kép (;;) sau mỗi trường hợp.

#Cú pháp lựa chọn trong bash shell
select item in list
do
  command
done

#Làm việc với các chuỗi
strings="Blogd.net"
Chúng ta có thể lấy chiều dài của chuỗi bằng cách sử dụng ${#strings}.

#Sử dụng mảng
Mảng là một danh sách các mục, được khai báo bên trong dấu ngoặc đơn như sau:
a=("di bien" "an uong" "di nui" "xem phim" "the thao")

có thể tham chiếu bất kỳ mục nào trong một mảng bằng dấu ngoặc vuông:
a[0]

có thể nhận được tổng số mục trong một mảng bằng cú pháp này:
${#a[@]}

#use function
function name {

}
examp : 
function test1(){
echo "Toi rat thich blogd.net"
}
test1

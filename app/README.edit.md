#cakePHP使用する際の留意点
デフォルトだと
・ControllerはControllerディレクトリ直下のControllerクラスしか走査しない
・ViewはViewsディレクトリ直下のController名のディレクトリ内しか走査しない

というクソ仕様。
これを
---------------------------------------------------------------
【Controller】
#クラス名
ゲーム側ファイル
クラス名 Public*****Controller

管理側ファイル
クラス名 Admin******Controller

#設置場所
ゲーム側ファイル
ROOT_DIR/app/Controller/Public/******/Public******Controller

管理側
ROOT_DIR/app/Controller/Admin/******/Admin******Controller


【View】
#設置場所
ゲーム側ファイル
ROOT_DIR/app/Views/Public/******/Public******/各アクション

管理側ファイル
ROOT_DIR/app/Views/View/******/View******/各アクション
---------------------------------------------------------------

にアクセスできるようにする
以下の【環境設定】をお願いします。

#環境設定
cake側にControllerとViewsディレクトリ内で走査して欲しい
ディレクトリを教えてあげる

app/Config/bootstrap.phpにて

/*
	Control
*/

// ゲーム側
// ログイン
App::build(array(
	'Controller' => array(ROOT.DS.APP_DIR.DS.'Controller'.DS.'Public'.DS.'Login'.DS),
));

// コントローラはアクションの分だけここに記述していく



/*
	View
*/
// 管理側
//ログイン
App::build(array(
	'views' => array(ROOT.DS.APP_DIR.DS.'View'.DS.'Public'.DS.'Login'.DS),
));


// ビューはアクションの分だけここに記述していく





# **Heroku 部署上線**

* 創建 Heroku App，並同時命名。

```
$ heroku create <專案名稱>
```

* 重新命名 Heroku App。

```
$ heroku apps:rename <新的專案名稱>
```

* 將主幹（master）進度部署至 Heroku。

```
$ git push heroku master
```

* 將分支（branch）進度部署至 Heroku。

```
$ git push <分支名稱>:master
```

* 執行所有 Migration。

```
$ heroku run rake db:migrate
```

<br/>

# **查看設定 & 歷程**

- 檢查專案的遠端路徑（ GitHub、Heroku）。

```
$ git remote -v
```

- 查看歷程（Logs）。

```
$ heroku logs
```

<br/>

# **Heroku 正式端資料**

* 使用遠端 Rails Console，可用於：新增或修改資料，操作方式與本地的 Rails Console 相同，輸入 `$ exit` 可以跳出。

```
$ heroku run rails console
```

* 利用 seed.rb 檔案內容創建資料。

```
$ heroku run rake db:seed
```

* 清空資料庫

```
$ heroku pg:reset DATABASE
```

<br/>

# **Heroku 版本復原**

## **Step 1. 查看過去的部署版本**

輸入後，終端機會列出所有的版本號（每一次推 Heroku 會是一版），找到要倒回的版號。

* 查看部署歷程。

```
$ heroku releases
```

從版本號歷程，你可以看到幾個部分：
。 版本號
。 部署內容
。 部署者
。 日期 / 時間

## **Step 2. 將 Heroku App 復原至該版本**

接著只要利用指令，倒回至該版本的內容即可。

* 將 Heroku 復原至過去的版本內容。

```
$ heroku rollback <版本號>
```

<br/>

# **Heroku 多人協作**

多人協作時，要讓其他開發人員一起參與 Heroku 的部署，可以照著以下步驟：


## **Step 1. Heroku App 的擁有者（Owner）將該人員加至協作者（Collaborator）名單**

* 終端機執行指令

```
$ heroku access:add <電子郵件地址>
```

## **Step 2. 協作者在本地設定 Heroku 遠端路徑。**

協作者會收到一封 Email，通知已經被加入協作名單。這時候只要為本機的專案添加 Heroku 的遠端路徑，就可以參與部署了。

- 新增專案的 Heroku 遠端路徑。

```
$ heroku git:remote -a <專案名稱>
```

<br/>

## **補充 — 協作相關指令**

* 瀏覽擁有權限的協作成員名單。

```
$ heroku access
```

* 移除協作成員。

```
$ heroku access:remove <電子郵件地址>
```

<br/>
<hr/>

##### 來源：

<a href="http://anndo-blog.logdown.com/" target="_blank"> Anndo </a>

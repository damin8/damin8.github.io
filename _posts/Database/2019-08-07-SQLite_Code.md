---
layout:     post
title:      "SQLite"
subtitle:   "SQLite 코드"
date:       2019-08-07 18:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Database
tags:
  - Database
---

## SQLite 코드

***In C#***

~~~
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.SQLite;
namespace SQLite
{
    class Test
    {
        static void Main(string[] args)
        {
            SQLiteConnection.CreateFile(@"Chatting");
            SQLiteConnection conn = new
                SQLiteConnection(@"Data Source=Chatting;Version=3");
                conn.Open();
                string query = "create table chatting (receiver varchar(20),sender varchar(20))";
                SQLiteCommand command = new SQLiteCommand(query, conn);
                int result = command.ExecuteNonQuery();

                query = "insert into chatting (receiver,sender) values ('안녕하세요 저는 신다민입니다','Damin')";
                command = new SQLiteCommand(query, conn);
                result = command.ExecuteNonQuery();

                query = "select * from chatting";

                command = new SQLiteCommand(query, conn);
                SQLiteDataReader reader = command.ExecuteReader();
                while (reader.Read())
                {
                    Console.WriteLine(reader["sender"].ToString());
                    Console.WriteLine(reader["receiver"].ToString());
                }
                reader.Close();
                conn.Close();
        }

    }
}

~~~

SQLite File을 만들어서, 그 안을 DB처럼 사용하였다.

요 앞전에 설명한것처럼 SQLite는 파일처럼 가볍고, 따로 서버가 존재할 필요가 없다.

따라서 대화목록같은것들을 저장하기 좋다.

연습삼아 해본거라 정말 쉬워보이지만, 막상 해보니 정말 시간이 오래걸렸던 작업이었다.

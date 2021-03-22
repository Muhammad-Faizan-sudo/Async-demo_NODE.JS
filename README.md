# Async-demo_NODE.JS

//simple callback

console.log('Before');
getUser(122, function(Userinfo){
    console.log(Userinfo);
});

console.log('After');

function getUser(id, callback){
    setTimeout(()=>{
        console.log('Reading a user from database...');
        callback({id:id, githubuserName: 'Muhammad Faizan'});
    }, 2000); 
}

Exp 2
//simple callback //due to nested function asyn it is not easy read and understand these type of code.....so thats why this type of code is called callback Hell OR CHRITMIS TREE

//CODE
console.log('Before');
getUser(122, (Userinfo) => {
    console.log(Userinfo);
    getRepositories(Userinfo.githubuserName, (UserRepo) => {
        console.log(UserRepo);
    });
});

console.log('After');

function getUser(id, callback){
    setTimeout(()=>{
        console.log('Reading a user from database...');
        callback({id:id, githubuserName: 'Muhammad Faizan'});
    }, 2000); 
}

function getRepositories(username,callback){
    setTimeout(()=>{
        console.log('Calling Github API...');
        callback(['repo1', 'repo2', 'repo3']);
    },2000); 
}

3- Example
//simple callback
//due to nested function asyn it is not easy read and understand these type of code.....so thats why this type of code is called callback Hell OR CHRITMIS TREE
//ANANOMOUS FUNCTION : FUNCTION WITHOUT NAME
console.log('Before');

getUser(122, DisplayUserInfo);

function displayCommits(commits)
{
    console.log(commits);
}

function DisplayRepositries(UserRepo)
{
    console.log(UserRepo);
    getCommits(UserRepo[0], displayCommits);
}

function DisplayUserInfo(Userinfo)
{
    getRepositories(Userinfo.githubuserName, DisplayRepositries);
    console.log(Userinfo);
}

console.log('After');

function getUser(id, callback){
    setTimeout(()=>{
        console.log('Reading a user from database...');
        callback({id:id, githubuserName: 'Muhammad Faizan'});
    }, 2000); 
}

function getRepositories(username,callback){
    setTimeout(()=>{
        console.log('Calling Github API...');
        callback(['repo1', 'repo2', 'repo3']);
    },2000); 
}

function getCommits(repo, callback) {
    setTimeout(() => {
      console.log('Calling GitHub API...');
      callback(['commit']);
    }, 2000);
  }

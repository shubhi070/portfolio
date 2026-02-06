// Typing effect
const roles = ["Frontend Developer", "React Developer", "UI Enthusiast"];
let i=0,j=0;
const typing = document.getElementById("typing");

function type(){
  if(j<roles[i].length){
    typing.textContent += roles[i][j++];
    setTimeout(type,100);
  } else {
    setTimeout(erase,1500);
  }
}
function erase(){
  if(j>0){
    typing.textContent = roles[i].substring(0,--j);
    setTimeout(erase,70);
  } else{
    i=(i+1)%roles.length;
    setTimeout(type,400);
  }
}
type();

// Scroll animation
const observer = new IntersectionObserver(entries=>{
  entries.forEach(entry=>{
    if(entry.isIntersecting){
      entry.target.classList.add("show");
    }
  });
});
document.querySelectorAll(".hidden").forEach(el=>observer.observe(el));

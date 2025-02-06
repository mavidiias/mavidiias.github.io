<script>
    let { img, title, text, botao } = $props();</script>
   <div class="card mb-3" style="max-width: 540px;">
       <div class="row g-0">
         <div class="col-md-4">
           <img src={img} class="img-fluid rounded-start" alt="invisibility">
         </div>
         <div class="col-md-8">
           <div class="card-body">
             <h5 class="card-title">{title}</h5>
             <p class="card-text">{text}</p>
             <a href={botao} class="stretched-link"></a>
           </div>
         </div>
       </div>
     </div>
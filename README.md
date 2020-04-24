  feesAndCharges: DS.belongsTo('product-pricing'),
  productInsuranceImg: DS.attr('string'),
  insuranceBannerContent: DS.attr('string'),
  insuranceFindMore: DS.attr('string'),
  insuranceTextTc: DS.attr('string')




.insuranceBanner{
  position: relative;
  padding: 10px;
  background-color: white;
  color: black;
  margin: 10px;
  border-radius: 5px;
  h6{
    font-size: 15px;
    font-weight: normal;
    color: #000;
    margin: 0;
  }
  p{
    font-size: 13px;
    font-weight: normal;
  }
  .insurance-more{
    margin-top: 10px;
    font-size: 12px;
    line-height: normal;
    color: #0091ea;
    letter-spacing: normal;
    font-weight: normal;
  }
  .insurance-tc{
    font-size: 10px;
    color: gray;
    margin-left: 10%;
  }
  img{
    width: 74px;
    height: 50px;
    object-fit: contain;
    position: absolute;
    bottom: 0px;
    right: -9px;
    margin-bottom: -8px;
  }  
}




    {{#if data.insuranceBannerContent}}
      <div class="insuranceBanner">
        <div class="insurance-content">
        {{{data.insuranceBannerContent}}}
      </div>
      <div class='insurance-more'>
        <span {{action send "insuranceBanner"}}>{{{data.insuranceFindMore}}}</span>
        <span class='insurance-tc'>{{{data.insuranceTextTc}}}</span>
      </div>
        <img src={{data.productInsuranceImg}} alt="Img"/>
      </div>
    {{/if}}
